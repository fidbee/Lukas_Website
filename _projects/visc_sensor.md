---
layout: page
title: Characeterizing a MEMS Viscosity Sensor
description: Design of a test setup and data collection.
img: assets/img/projects/visc_sensor/sensors_in_oven.jpg
related_publications: true
importance: 3
category: Other
---

During my first summer at RIT I did research in the lab of Dr. Ivan Puchades at RIT. My project focussed on characterizing the sensitivity of existing MEMS viscometers based on a variety of metrics. This involved the creation of a new test setup to improve signal quality. The five different types of sensors were then tested at various viscosities to characterize their performance.

FILTERING CIRCUIT AND BETTER RESULTS

I made two major improvements to the test setup. The first was the design of a cricuit to filter and amplify the output signal. This removed a lot of the noise in the 

SENSOR IN AIR + GRAPH OF DATA
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/visc_sensor/sensor_in_air.jpg" title="sensor_in_air" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/visc_sensor/sensor_in_air_data.png" title="sensor_in_air_data" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    This image can also have a caption. It's like magic.
</div>

In order to measure the performance of the sensors at varying levels of viscosity, the temperature of the fluids was changed. However, this change in temperature also affects the performance of the sensor for other reasons. Thus, the temperature effect on the sensor had to first be subtracted out. To do this, the sensors were first tested in air as temperature changed. Because the viscosity of air does not change much with temperature, this isolates only the temperature effects on the sensor. The sensor was strapped to a heat sink to decrease noise and provide more consistent readings. From here, the percent change in FFT frequency per °C was calculated and used to adjust our viscosity data as temperature changed.






