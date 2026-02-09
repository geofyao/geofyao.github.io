---
title: "E5 Nexus Lab — misc"
layout: textlay
excerpt: "E5 Nexus Lab — misc"
sitemap: false
permalink: /gc-pvlib-Li.html
---

This page describes the variables required to calculate the impacts of particulate matter (PM) on solar photovoltaic (PV) efficiency or capacity factor (`CF` \[unitless\]). To calculate the impacts of fine particulate matter (PM<sub>2.5</sub>) on public health, only PM<sub>2.5</sub> concentrations \[µg m<sup>-3</sup>\], are needed.


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

***We distinguish between gravitational and turbulent deposition fluxes**, as gravitational deposition is reduced on tilted panels whereas turbulent deposition is not. These fluxes may also be derived from the product of deposition velocities (`GraDepVel_spe` and `TurDepVel_spe`) and near-surface aerosol concentrations (`AerMass`). For aerosol species, **we require at least a separation between secondary inorganic aerosols (sulfate + nitrate + ammonia), black carbon, organic carbon, and dust** because of their different optical effects on solar panels. More detailed speciation is acceptable, as it can be aggregated within the coupling code.*

`precipitation_rates`: precipitation rates at the ground \[mm h<sup>-1</sup>\]

---

`temp_air`: Air temperature (also known as dry-bulb temperature) \[C\]

`wind_speed`: Wind speed at a height of 10 meters \[m/s\]
