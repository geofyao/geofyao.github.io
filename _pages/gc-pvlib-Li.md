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

`temp_air`: Air temperature (also known as dry-bulb temperature) \[C\]

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

XXX

