---
layout: page
title: Argon Gas Cooling Using Liquid Nitrogen
description: Analysis and simulation of a mechanism to cool argon gas.
img: assets/img/projects/ln2_cooling/liquid_nitrogen_pour.jpg
importance: 3
category: Laboratory for Laser Energetics
---

An argon gas cooling setup was designed by a previous intern at the Laboratory for Laser Energetics (LLE). The mechanism is meant to cool a stream of argon from room temperature to ~90K, just above the 83K melting point with some room for error. With liquid nitrogen (LN<sub>2</sub>) being easily accessible and at 77K, it was used to provide the cooling. The device was built, but the end user reported concerns about a temperature gradient across the spool causing inconsistent temperature results. My role in this project was to investigate the cause of this, develop a more accurate model of the system, and use this to make any necessary changes. At the time, I was working part time at LLE while taking classes.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/ln2_cooling/liquid_nitrogen_pour.jpg" title="liquid_nitrogen_pour" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/ln2_cooling/pack_column_diagram.jpg" title="pack_column_diagram" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Left: Pouring liquid nitrogen in the experimental setup to get initial temperature measurements. <br>
    Right: Annotated diagram of the overall system.
</div>

I started by making two improvements to the setup. <br>
1. There were small gaps in some of the copper connections. I filled these with indium strips to improve thermal contact. <br>
2. The cap being used on the original setup was just a ball of aluminum foil placed on top of the dewar. I replaced this with a machined XPS foam cap with a few holes for venting and thermocouple wires.

<div class="row justify-content-sm-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/ln2_cooling/tc_locations.jpg" title="tc_locations" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/ln2_cooling/taped_thermocouple.jpg" title="taped_thermocouple" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Left: Several thermocouples were placed along each copper body. <br>
    Right: Kapton tape combined with aluminum tape ensured a strong thermal contact on the thermocouples. Care was taken to eliminate air bubbles.
</div>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/ln2_cooling/packed_col_results.jpg" title="packed_col_results" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Some initial thermocouple results of the transient cooldown and steady state portion. Relevant points labeled.
</div>

I taped several thermocouples on various parts of the setup to get an idea of how the system is behaving. I was interested in the time it takes to cool down, and the temperature of the spool while the LN<sub>2</sub> was in contact with the dip tube. The temperature of the spool was within an acceptable margin of error with a small temperature gradient across it. Overall, these results were pretty good, but I still wanted to create a more accurate model of the system to figure out what could be changed to improve performance. I ran this test several more times to get enough data to start improving the simulation model. 

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/ln2_cooling/original_model.jpg" title="original_model" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    The original model had the gaseous and liquid LN<sub>2</sub> modeled as solid bodies without any convection.
</div>

The existing model was a good baseline but did not align well with experimental data, especially during the steady state. The biggest issue was the lack of convection. While conduction is the dominant form of heat transfer here, the evaporating nitrogen meant that convection was not negligible. Additionally, the assumption of the top surface of the dewar being at exactly room temperature was proven to not be true after measurement.

I made a few assumptions to simplify the model. The area between the LN<sub>2</sub> and the XPS foam cap was assumed to be pure, ideal, and uncirculating nitrogen gas. At this stage, thermal contacts were still assumed to be bonded. The delrin supports were also assumed to have negligible heat transfer.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/ln2_cooling/convection_equations.jpg" title="convection_equations" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Natural convection equations that I used to estimate convective coefficients.
</div>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/ln2_cooling/packed_col_ansys_setup.jpg" title="packed_col_ansys_setup" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Overall setup of the new model that I created.
</div>

Because the nitrogen gas was assumed to be still, I used natural convection equations found in my heat transfer textbook to estimate convection coefficient for each body in the system. At this point, I also moved the thermocouples to hang at various heights throughout the gaseous nitrogen. This gave me an estimate of the ambient temperature profile as a function of distance from the LN<sub>2</sub> surface (T<sub>inf</sub>). A combination of measured data and tabular values allowed me to estimate the convection coefficients on the relatively simple geometry. I created a new model that included convection and made a few other small changes. The solid body nitrogen was instead modeled as a set of boundary conditions and various mesh areas were either refined or derefined to improve performance and accuracy.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/ln2_cooling/transient_results.jpg" title="transient_results" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Transient cooldown comparison between models. The new convective model had much stronger agreement with the experimental data, but there was still room for improvement.
</div>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/ln2_cooling/packed_col_visual_results.png" title="packed_col_visual_results" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Some visual results showing potential areas of improvement if a cooler temperature is desired.
</div>

Overall the new model has much stronger correlation with the experimental data. It accurately captured the transient cooldown and was within ~3K during the steady state portion. There are many areas to improve here, this is what I thought would be most significant: <br>

1. Modeling of changing LN<sub>2</sub> level: I think this is the biggest source of error. In the experimental data, the steady state varies by several degrees as the LN<sub>2</sub> evaporates. I think I could've taken more experimental data and made the 77K LN<sub>2</sub> boundary condition a parameter in the simulation that varies over time to more accurately capture the steady state. <br>
2. More accurate fill level: Even when used in the lab, the LN<sub>2</sub> is just filled to a Kapton tape line in the dewar. This is a big source of variation between trials. <br>
3. Bonded thermal contact assumption: Clamping indium between copper creates a very good thermal contact, but I still think that there is non-negligible contact resistance here. This is a value that could be measured or tweaked in the model to get a more accurate simulation. <br>

Regardless, the end user was satisfied with the results he was seeing after the small improvements that were made. My model provides a baseline for future changes and similar projects. This project was my first exposure to thermal modeling in ANSYS. I found the combination of experimental data collection, hand calculations, and simulation rewarding and hope to work on similar projects in the future.
