---
title: "E5 Nexus Lab — Research"
layout: textlay
excerpt: "E5 Nexus Lab — Research"
sitemap: false
permalink: /research/
---

**~~Life~~Research is like riding a bicycle. To keep your balance, you must keep moving. — Albert Einstein**

---

We focus on interdisciplinary research in environmental and Earth sciences, with an emphasis on [1) atmospheric environment, its impacts, and responses](#1-atmospheric-environment-its-impacts-and-responses--大气环境及影响与应对), [2) renewable energy and climate change mitigation](#2-renewable-energy-and-climate-change-mitigation--可再生能源与减缓气候变化), and [3) AI-enabled sustainable energy and environmental research](#3-ai-enabled-sustainable-energy-and-environmental-research--ai赋能可持续能源与环境研究). We use a range of research approaches, including emission inventories and input–output models (GTAP); global and regional atmospheric chemical transport models (GEOS-Chem, WRF-GC, etc.) equipped with radiative transfer modules (RRTMG); solar photovoltaic performance models (PVLIB-Python); health impact models (Global Burden of Disease, GBD); adjoint modelling; and machine learning and statistical methods. The work that we have done/currently do/will do includes but is not limited to the following:

课题组长期致力于环境与地球科学领域交叉学科研究，重点关注[（1）大气环境影响及应对](#1-atmospheric-environment-its-impacts-and-responses--大气环境及影响与应对)、[（2）可再生能源与减缓气候变化](#2-renewable-energy-and-climate-change-mitigation--可再生能源与减缓气候变化)、以及[（3）AI赋能可持续能源与环境研究](#3-ai-enabled-sustainable-energy-and-environmental-research--ai赋能可持续能源与环境研究)。主要研究手段包括排放清单和投入产出模型（GTAP）、配备辐射传输模块（RRTMG）的全球和区域尺度大气化学传输模式（GEOS-Chem, WRF-GC等）、太阳能光伏发电模型（PVLIB-Python）、健康效应模型（Global Burden of Disease, GBD）、伴随模式（Adjoint modelling）、机器学习和统计方法等。已完成/正在进行/将要开展的工作包括但不限于：

---

#### **1\. Atmospheric environment, its impacts, and responses \| 大气环境及影响与应对**

As illustrated in the figure below, our research addresses a conceptual system in which natural and anthropogenic activities generate **emissions** of air pollutants and greenhouse gases. These constituents are transported and transformed in the atmosphere, ultimately influencing solar energy generation, public health, and ecosystem health, among other **impacts**. In **response** to these environmental effects, policy interventions are implemented, which in turn can modify emissions. Our research examines this conceptual system as a whole, while also investigating its individual components.

<div style="text-align: center; margin: 10px 0;">
  <img src="{{ site.url }}{{ site.baseurl }}/images/respic/E5_Nexus_Lab.jpg" style="width: 80%;">
</div>

##### **1.1. Drivers of atmospheric environmental variations and their impacts on energy, public health, and ecosystem health \| 大气环境变化的驱动因素及其对能源与健康的影响**

We integrate models from multiple disciplines to describe the conceptual system outlined above. Using this integrated approach, we perform counterfactual experiments to identify the socioeconomic and natural drivers behind the impacts of atmospheric environmental variations on energy, public health, and ecosystem health. The identified drivers provide guidance for effectively mitigating these environmental impacts.

<div style="text-align: center; margin: 10px 0;">
  <img src="{{ site.url }}{{ site.baseurl }}/images/respic/interdisciplinary_framework.jpg" style="width: 80%;">
</div>

Refs:

**<u>Socioeconomic drivers:</u>**

<b>Yao, F.<sup>\*</sup></b>, Palmer, P.I., Liu, J., Chen, H. and Wang, Y., 2025. Attribution of Solar Energy Yield Gaps due to Transboundary Particulate Matter Pollution Associated with Trade across Northeast Asia. <i>Environmental Science & Technology</i>, 59(29), pp.15092-15100. doi: [10.1021/acs.est.5c05935](https://pubs.acs.org/doi/10.1021/acs.est.5c05935)

<div style="text-align: center; margin: 10px 0;">
  <img src="{{ site.url }}{{ site.baseurl }}/images/respic/yao2025attribution.png" style="width: 80%;">
</div>

<b>Yao, F.<sup>\*</sup></b> and Palmer, P.I., 2022. Source Sector Mitigation of Solar Energy Generation Losses Attributable to Particulate Matter Pollution. <i>Environmental Science & Technology</i>, 56(12), pp.8619-8628. doi: [10.1021/acs.est.2c01175](https://pubs.acs.org/doi/full/10.1021/acs.est.2c01175)
<br/>
[gc-pvlib-Li](https://geofyao.github.io/multifaceted-impacts-quantification.html#21-my-gc-pvlib-lipy-that-can-consider-both-pm-dimming-and-soiling)

<div style="text-align: center; margin: 10px 0;">
  <img src="{{ site.url }}{{ site.baseurl }}/images/respic/yao2022source.png" style="width: 50%;">
</div>

Liu, J.<sup>#</sup>, <b>Yao, F.<sup>#</sup></b>, Chen, H.<sup>\*</sup> and Zhao, H.<sup>\*</sup>, 2025. Quantifying the Source–Receptor Relationships of PM<sub>2.5</sub> Pollution and Associated Health Impacts among China, South Korea, and Japan: A Dual Perspective and an Interdisciplinary Approach. <i>Environmental Health Perspectives</i>, 133(3-4), p.047011. doi: [10.1289/EHP14550](https://pmc.ncbi.nlm.nih.gov/articles/PMC12036670/)

<div style="text-align: center; margin: 10px 0;">
  <img src="{{ site.url }}{{ site.baseurl }}/images/respic/liu2025quantifying.jpg" style="width: 80%;">
</div>

Liu, J.<sup>\*</sup>, Li, J. and Yao, F., 2022. Source-receptor relationship of transboundary particulate matter pollution between China, South Korea and Japan: Approaches, current understanding and limitations. <i>Critical Reviews in Environmental Science and Technology</i>, 52(21), pp.3896-3920. doi: [10.1080/10643389.2021.1964308](https://doi.org/10.1080/10643389.2021.1964308)

**<u>Natural drivers (including interactions with socioeconomic drivers):</u>**

Yin, K.<sup>#</sup>, <b>Yao, F.<sup>#</sup></b>, Luo, N., Gao, M., Lu, X.<sup>\*</sup> and Yi, B.<sup>\*</sup>, 2026. Substantial reduction of solar photovoltaic potential in China by an extreme dust event. <i>Communications Earth & Environment</i>, 7(1), p.44. doi: [10.1038/s43247-025-03123-1](https://doi.org/10.1038/s43247-025-03123-1)

<div style="text-align: center; margin: 10px 0;">
  <img src="{{ site.url }}{{ site.baseurl }}/images/respic/yin2026substantial.webp" style="width: 80%;">
</div>

##### **1.2. Atmospheric environment simulation and satellite remote sensing monitoring \| 大气环境模拟与卫星遥感监测**

We use both process-based models (e.g., GEOS-Chem) and statistical and machine learning methods to track emissions (e.g., NO<sub>x</sub>) that drive atmospheric environmental conditions near the surface (e.g., PM<sub>2.5</sub> concentrations), which are most relevant to public health. We combine these ground-level environmental estimates with individual mobility and socioeconomic data to examine disparities in exposure across different population groups. The research findings inform atmospheric environmental management policies and environmental equity efforts.

Refs:

**<u>Emissions:</u>**

Stay tuned.

**<u>Atmospheric environmental conditions (PM<sub>2.5</sub> concentrations):</u>**

<b></b> Liu, J., Zheng, Z., <b>Yao, F.<sup>\*</sup></b> and Li, W.<sup>\*</sup>, 2026. A multi-view machine learning approach for estimating PM<sub>2.5</sub> concentrations from smartphone photographs. <i>Journal of Hazardous Materials</i>, 511, p.142172. doi: [10.1016/j.jhazmat.2026.142172](https://doi.org/10.1016/j.jhazmat.2026.142172)

<div style="text-align: center; margin: 10px 0;">
  <img src="{{ site.url }}{{ site.baseurl }}/images/respic/liu2026multiview.jpg" style="width: 80%;">
</div>

<b>Yao, F.<sup>\*</sup></b> and Palmer, P.I., 2021. A model framework to reduce bias in ground-level PM<sub>2.5</sub> concentrations inferred from satellite-retrieved AOD. <i>Atmospheric Environment</i>, 248, p.118217. doi: [10.1016/j.atmosenv.2021.118217](https://www.sciencedirect.com/science/article/pii/S1352231021000352)

<div style="text-align: center; margin: 10px 0;">
  <img src="{{ site.url }}{{ site.baseurl }}/images/respic/yao2021model.jpg" style="width: 80%;">
</div>

<b>Yao, F.</b>, Wu, J.<sup>\*</sup>, Li, W.<sup>\*</sup> and Peng, J., 2019. A spatially structured adaptive two-stage model for retrieving ground-level PM<sub>2.5</sub> concentrations from VIIRS AOD in China. <i>ISPRS Journal of Photogrammetry and Remote Sensing</i>, 151, pp.263-276. doi: [10.1016/j.isprsjprs.2019.03.011](https://www.sciencedirect.com/science/article/pii/S0924271619300814)

<b>Yao, F.</b>, Wu, J.<sup>\*</sup>, Li, W. and Peng, J., 2019. Estimating daily PM<sub>2.5</sub> concentrations in Beijing using 750-M VIIRS IP AOD retrievals and a nested spatiotemporal statistical model. <i>Remote Sensing</i>, 11(7), p.841. doi: [10.3390/rs11070841](https://www.mdpi.com/2072-4292/11/7/841)

<b>Yao, F.</b>, Si, M., Li, W.<sup>\*</sup> and Wu, J.<sup>\*</sup>, 2018. A multidimensional comparison between MODIS and VIIRS AOD in estimating ground-level PM<sub>2.5</sub> concentrations over a heavily polluted region in China. <i>Science of the Total Environment</i>, 618, pp.819-828. doi: [10.1016/j.scitotenv.2017.08.209](https://www.sciencedirect.com/science/article/pii/S0048969717322076)

Wu, J., Yao, F., Li, W.<sup>\*</sup> and Si, M., 2016. VIIRS-based remote sensing estimation of ground-level PM<sub>2.5</sub> concentrations in Beijing–Tianjin–Hebei: A spatiotemporal statistical model. <i>Remote Sensing of Environment</i>, 184, pp.316-328. doi: [10.1016/j.rse.2016.07.015](https://www.sciencedirect.com/science/article/pii/S0034425716302735)<br/>
Supervisor as first author

Guo, H., Li, W.<sup>\*</sup>, Yao, F., Wu, J., Zhou, X., Yue, Y. and Yeh, A.G., 2020. Who are more exposed to PM<sub>2.5</sub> pollution: A mobile phone data approach. <i>Environment International</i>, 143, p.105821. doi: [10.1016/j.envint.2020.105821](https://www.sciencedirect.com/science/article/pii/S0160412020317761)

**<u>Atmospheric environmental conditions (urban heat island):</u>**

Wang, Y., Wang, H., <b>Yao, F.<sup>\*</sup></b>, Stouffs, R. and Wu, J.<sup>\*</sup>, 2024. An integrated framework for jointly assessing spatiotemporal dynamics of surface urban heat island intensity and footprint: China, 2003–2020. <i>Sustainable Cities and Society</i>, 112, p.105601. doi: [10.1016/j.scs.2024.105601](https://doi.org/10.1016/j.scs.2024.105601)

##### **1.3. Trade-offs and synergies in mitigating multiple atmospheric environmental impacts \| 多重大气环境影响减缓的权衡与协同效应**

Stay tuned.

---

#### **2\. Renewable energy and climate change mitigation \| 可再生能源与减缓气候变化**

##### **2.1. Satellite remote sensing monitoring of renewable energy infrastructure \| 可再生能源基础设施卫星遥感监测**

Stay tuned.

##### **2.2. Environmental impact analysis of renewable energy infrastructure \| 可再生能源基础设施环境影响分析**

Stay tuned.

---

#### **3\. AI-enabled sustainable energy and environmental research \| AI赋能可持续能源与环境研究**

The research areas listed above involve the use of AI to varying degrees, and we will continue to explore and expand the application of AI in these and other research directions.

---

#### **4\. More innovative research directions and scientific questions await your exploration! \| 更多有趣的研究方向和科学问题等你来提出！**
