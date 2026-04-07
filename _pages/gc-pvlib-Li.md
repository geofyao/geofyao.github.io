---
title: "E5 Nexus Lab — misc"
layout: textlay
excerpt: "E5 Nexus Lab — misc"
sitemap: false
permalink: /gc-pvlib-Li.html
---

This page describes the variables required to calculate the impacts of particulate matter (PM) on solar photovoltaic (PV) efficiency or capacity factor (`CF` \[unitless\]). Depending on the availability of solar PV facility data and their installed capacities, actual solar PV power generation losses can also be calculated. To calculate the impacts of fine particulate matter (PM<sub>2.5</sub>) on public health, only PM<sub>2.5</sub> concentrations \[µg m<sup>-3</sup>\], are needed.

### `gc-pvlib-Li.py` that considers both PM dimming and soiling:

<div style="text-align: center; margin: 10px 0;">
  <img src="{{ site.url }}{{ site.baseurl }}/images/respic/gc-pvlib-Li_en.png" style="width: 100%;">
</div>

**Each data record <u>must</u> contain coordinates for latitude, longitude, and UTC time, as well as the following variables:**

`GHI`: Global Horizontal Irradiance \[W/m<sup>2</sup>\]

`DNI`: Direct Normal Irridance \[W/m<sup>2</sup>\]

`DHI`: Diffuse Horizontal Irradiance \[W/m<sup>2</sup>\]

*Note that models like GEOS-Chem may provide only `GHI`; in such cases, we use the Erbs model (or similar methods) to estimate `DNI` and `DHI` from `GHI`.*

---

`pressure`: Air pressure \[Pa\] to help determine altitude from sea level \[m\] and to adjust solar position and air mass estimates.

<!-- altitude + pressure + temperature -> solarposition; solarposition -> airmass_relative -> total_irrad; airmass_relative + pressure -> airmass_absolute -->

`albedo`: reflectivity of the ground surface \[unitless\]

---

`GraDepFlux_spe`: gravitational deposition flux of a specific aerosol species \[g m<sup>-2</sup>\]

`TurDepFlux_spe`: turbulent deposition flux of a specific aerosol species \[g m<sup>-2</sup>\]

_**We distinguish between gravitational and turbulent deposition fluxes**, as gravitational deposition is reduced on tilted panels whereas turbulent deposition is not. These fluxes may also be derived from the product of deposition velocities (`GraDepVel_spe` and `TurDepVel_spe`) and near-surface aerosol concentrations (`AerMass`). For aerosol species, **we require at least a separation between secondary inorganic aerosols (sulfate + nitrate + ammonia), black carbon, organic carbon, and dust** because of their different optical effects on solar panels. More detailed speciation is acceptable, as it can be aggregated within the coupling code. ~~If gravitational and turbulent deposition fluxes/velocities cannot be readily distinguished, we consider separate them using aerosol composition. For instance, coarse dust particles are predominantly associated with gravitational settling, whereas other species are mainly governed by turbulent deposition. Relevant supporting literature will be required, though~~._

`precipitation_rates`: precipitation rates at the ground \[mm h<sup>-1</sup>\]

---

`temp_air`: Air temperature (also known as dry-bulb temperature) \[$^{\circ}$C\]

`wind_speed`: Wind speed at a height of 10 meters \[m/s\]

---

Among the five meteorological variables listed above, `temp_air` and `pressure` are primarily used to adjust solar position and air mass estimates, which may influence irradiance (for example, the `perez` sky diffuse model requires air mass as an input), but should only to a limited extent. `albedo` changes very slowly; however, because it directly converts `GHI` to E<sub>g</sub>, it has a strong impact on irradiance. `precipitation` affects soiling and therefore irradiance. `temp_air` and `wind_speed` mainly affect cell temperature rather than irradiance.

**To isolate the effects of changing meteorological conditions on irradiance alone, we can keep `temp_air` and `wind_speed` the same as in the CTRL case while varying the other variables as needed.** The only drawback of this approach is that `temp_air` may slightly affect the solar position, and therefore irradiance, calculations. However, this impact should be minimal (see discussion <a href="https://github.com/pvlib/pvlib-python/issues/1065#issuecomment-697640969">here</a>). Hence, we may not supply an alternative `temp_air` source specifically for solar position calculations in both `gc-pvlib-Li.py` and `modelchain.py`, as outlined below:

```python

solar_position = location.get_solarposition(index,
                                            pressure=pressure,
                                            temperature=temp_air)

---

# build kwargs for solar position calculation
try:
    press_temp = _build_kwargs(['pressure', 'temp_air'], weather)
    press_temp['temperature'] = press_temp.pop('temp_air')
except KeyError:
    pass
self._prep_inputs_solar_pos(kwargs=press_temp) # press_temp => kwargs=press_temp for readability.

```

---

`grid_indices`: indices of the grid cells included in the parallel calculations. This is optional but can improve performance by restricting computations to selected areas (e.g., land grids only).


### Alternative empirical methods that consider only PM dimming:

On the other hand, most studies examing the impacts of climate change and/or carbon neutrality on solar PV efficiency or capacity factor (`CF`, \[unitless\]) have primarily focused on the effects of PM dimming, while neglecting soiling. **In such cases, only downward shortwave radiation ($I$, W m$^{-2}$), ambient temperature at 2 m ($T_{2m}$, $^{\circ}$C), and wind speed at 10 m ($u_{10m}$, m s$^{-1}$) are required:**

$$
CF = P_R \frac{I}{I_{STC}},
$$

where STC refers to the standard test conditions ($I_{STC}=1000$ W m$^{-2}$), those for which the nominal capacity of a PV devive is determined as its measured power output, and $P_R$ is the so-called performance ratio, formulated to account for changes of the PV cells efficiency due to changes in their temperature as:

$$
P_R = 1 - \gamma (T_{cell} - T_{STC}),
$$

where $T_{cell}$ in the PV cell temperature, $T_{STC}$=25 $^{\circ}$C and $\gamma$ is taken here as 0.005 $^{\circ}$C$^{-1}$, considering the typical response of monocrystalline silicon solar panels. Finally, Finally, $T_{cell}$ is modelled considering the effects of $T_{2m}$, $I$, and $u_{10m}$ on it as:

$$
T_{cell} = c_1 + c_2 T_{2m} + c_3 I - c_4 u_{10m},
$$

with $c_1 = 4.3^{\circ}C$, $c_2=0.943$, $c_3=0.028^{\circ}C (W~m^{-2})^{-1}$, $c_4=1.528^{\circ}C (m~s^{-1})^{-1}$.

Hence, if ambient conditions ($I$, $T_{2m}$ and $u_{10m}$) correspond to the STCs, `CF` equals 1 and PV power production reaches the rated value. If they are so that $T_{cell}$ is higher (lower) than 25 $^{\circ}$C and/or $I$ lower (higher) than 1,000 W m^{−2}, `CF` will be lower (higher) than the unit and the PV power output will be lower (higher) than the nominal power of the module.

All variables involved and their corresponding units are listed in the table below:

| Variable | Description | Units |
| --- | --- | --- |
| $I$ | Downward shortwave radiation | W m$^{-2}$ |
| $T_{2m}$ | Ambient temperature at 2 m | $^{\circ}$C |
| $u_{10m}$ | Wind speed at 10 m | m s$^{-1}$ |
| $I_{STC}$ | Shortwave radiation on PV panels under standard test conditions (1000 W m$^{-2}$) | W m$^{-2}$ |
| $P_R$ | Performance ratio | 1 |
| $T_{cell}$ | Cell temmperature | $^{\circ}$C |
| $T_{STC}$ | Cell temmperature under standard test conditions (25 $^{\circ}$C) | $^{\circ}$C |
| $\gamma$ | 0.005 | $^{\circ}$C$^{-1}$ |
| $c_1$ | 4.3 | $^{\circ}$C |
| $c_2$ | 0.943 | 1 |
| $c_3$ | 0.028 | $^{\circ}$C (W m$^{-2}$)$^{-1}$ |
| $c_4$ | 1.528 | $^{\circ}$C (m s$^{-1}$)$^{-1}$ |
| $CF$ | Capacity factor | 1 |
