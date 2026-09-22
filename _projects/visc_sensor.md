---
layout: page
title: Characterizing a MEMS Viscosity Sensor
description: Design of a test setup and data collection.
img: assets/img/projects/visc_sensor/sensors_in_oven.jpg
related_publications: false
importance: 3
category: Other
---

During my first summer at RIT, I did research in the lab of Dr. Ivan Puchades at RIT. My project focused on characterizing the sensitivity of existing MEMS viscometers. These sensors could provide a much more compact and portable measurement compared to traditional viscometers. This has potential applications in the active monitoring of oil health in engines. This project involved the creation of a new test setup to improve signal quality as well as the testing of five different types of sensors at various viscosities to characterize their performance. Some of the data I took on my new setup was also used in a [published paper](https://www.researchgate.net/publication/377943706_Waterproofing_a_Thermally_Actuated_Vibrational_MEMS_Viscosity_Sensor).

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/visc_sensor/sensor_diagram.jpg" title="sensor_diagram" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Diagram of sensors
</div>

The sensors are actuated by a central heater controlled by pulses from a waveform generator. This oscillates a 15μm silicone membrane. As the sensor is submerged in various fluids, the amplitude and frequency of these oscillations varies. Four strain gauge resistors arranged in a Wheatstone bridge provide this feedback. This provides estimates into the magnitude and frequency of the deflections. The five different types of sensors I was testing had various combinations of heater and strain gauge material as well as varying heater sizes.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/visc_sensor/filtering_circuit.jpg" title="filtering_circuit" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Amplification + filtering circuit
</div>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/visc_sensor/improved_signal.jpg" title="improved_signal" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Improvement in the consistency of data output on the improved setup. This is the output from the same sensor in the same conditions.
</div>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/visc_sensor/new_setup.jpg" title="new_setup" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Testing the new setup
</div>

I made two major improvements to the test setup. The first was the design of a circuit to filter and amplify the output signal. The high pass filtering removed a lot of the low frequency oscillations that caused unwanted spikes in our frequency spectrum. This also helped remove the DC offset seen in the graph above. The second improvement was switching the setup to a new oscilloscope with a higher sampling rate. Several improvements were made to the LabVIEW setup to modate these changes. Overall, the sensors produced a much more consistent output after these changes. The process of creating this setup made me much more comfortable with basic electronic equipment like waveform generators, power supplies, and oscilloscopes. 

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/visc_sensor/sensor_in_air.jpg" title="sensor_in_air" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/visc_sensor/sensor_in_air_data.png" title="sensor_in_air_data" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Sensors were first tested in air to remove the temperature effect on performance.
</div>

In order to measure the performance of the sensors at varying levels of viscosity, the temperature of various oils was varied using a lab oven. These oils have a predictable temperature to viscosity relationship. However, this change in temperature also affects the performance of the sensor for other reasons. Thus, this temperature effect on the sensor had to first be subtracted out. The sensors were first tested in air as temperature changed. Because the viscosity of air does not change much with temperature, this isolates only the temperature effects on the sensor. The sensor was strapped to a heat sink to decrease noise and provide more consistent readings. From here, the percent change in FFT frequency per °C was calculated and used to adjust our viscosity data as temperature changed.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/visc_sensor/N100_results.jpg" title="N100_results" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Comparison of 5 different types of sensors at various viscosities.
</div>

The sensors were tested in several lab mineral oils of varying viscosity. These were advantageous to traditional engine oil because of their predictable and well documented temperature to viscosity curves. In general, the sensors with larger heaters (T2, T3, T4) showed the largest frequency change per centistoke of viscosity. This is desirable to get the best estimate of a viscosity given an output frequency. Other metrics were also looked at, but the FFT frequency proved to have the most consistent change to a varying viscosity. 