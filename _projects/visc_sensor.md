---
layout: page
title: Characeterizing a MEMS Viscosity Sensor
description: Design of a test setup and data collection.
img: assets/img/projects/visc_sensor/sensors_in_oven.jpg
related_publications: true
importance: 3
category: Other
---

During my first summer at RIT I did research in the lab of Dr. Ivan Puchades at RIT. My project focussed on characterizing the sensitivity of existing MEMS viscometers. These sensors could provide a much more compact and portable measurement compared to traditional viscometers. This project involved the creation of a new test setup to improve signal quality as well as the testing of five different types of sensors at various viscosities to characterize their performance.

SENSOR DIAGRAM

The sensors are actuated by a central heater controlled by pulses from a waveform generator. This oscillates a 15μm silicone membrane. As the sensor is submerged in various fluids, the amplitude and frequency of these oscillations varies. Four strain gauge resistors arranged in a wheatstone bridge provide this feedback. This gives estimates into the magnitude and frequency of the deflections. The five different types of sensors I was testing had various combinations of heater and strain gauge material as well as varying heater sizes.

FILTERING CIRCUIT AND BETTER RESULTS

I made two major improvements to the test setup. The first was the design of a circuit to filter and amplify the output signal. The high pass filtering removed a lot of the low frequency oscillations that caused unwanted spikes in our frequency spectrum. This also helped remove the DC offset seen in the grpah above. The second improvement was migrating the setup to a new ossciloscope with a higher sampling rate. Several improvements were made to the LabVIEW setup to accomodate these changes. Overall, the sensors produced a much more consistent output after these changes.

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

N100 RESULTS

The sensors were tested in several lab mineral oils of varying viscosity. These were advantageous to traditional engine oil because of their predicatable and well documented temperature to viscosity curves. In general, the sensors with larger heaters (T2, T3, T4) showed the largest frequency change per centistoke of viscosity. This is desirable to get the best estimate of a viscosity given an output frequency. 