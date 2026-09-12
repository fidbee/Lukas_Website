---
layout: page
title: Argon Gas Cooling Using Liquid Nitrogen
description: Analysis and simulation of a mechanism to cool argon gas.
img: assets/img/projects/liquid_nitrogen_pour.jpg
importance: 4
category: Laboratory for Laser Energetics
---

An argon gas cooling setup was design by a previous intern at the Laboratory for Laser Energetics (LLE). The mechanism is meant to cool a stream of argon from room temperature to ~90K, just above the 83K melting point. With liquid nitrogen (LN<sub>2</sub>) being easily accessible and at 77K, it was used to provide cooling. The device was built, but end user reported concerns about a temperature gradient causing inconsistent temperature results. My role in this project was to investigate the cause of this, develop a more accurate model of the system, and use this to make any necessary changes. At the time, I was working part time at LLE while taking classes.

LN2 POUR AND ANNOTATED PHOTO
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/1.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/3.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/5.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Caption photos easily. On the left, a road goes through a tunnel. Middle, leaves artistically fall in a hipster photoshoot. Right, in another hipster photoshoot, a lumberjack grasps a handful of pine needles.
</div>

I started by making two improvements to the setup. <br>
1. There were small gaps in some of the copper connections. I filled these with indium strips to improve thermal contact. <br>
2. The cap being used on the original setup was just a ball of aluminum foil placed on top of the dewar. I replaced this with a machined XPS foam cap with a few holes for venting and thermocouple wires.

TAPED THERMOCOUPLE AND TC LOCATIONS
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/5.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    This image can also have a caption. It's like magic.
</div>
ANNOTATED GRAPH OF INITIAL TC RESULTS
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/5.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    This image can also have a caption. It's like magic.
</div>

I taped several thermocouples on various parts of the setup to get an idea of how the system is behaving. I was interested in the time it takes to cool down, and the temperature of the spool while the LN<sub>2</sub> was in contact with the dip tube. The temperature of the spool was within an acceptable margin of error with a small temperature gradient accross it. Overall, these results were pretty good, but I still wanted to create a more accurate model of the system to figure out what could be changed to improve performance. I ran this test several more times to get enough data to start improving the simulation model. 

ORIGINAL CONDCUTIVE MODEL WITH SOLID LN2
<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/6.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/11.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    You can also have artistically styled 2/3 + 1/3 images, like these.
</div>

The existing model was a good baseline but did not align well with experimental data, especially during the steady state. The biggest issue was the lack of convection. While conduction is the dominant form of heat transfer here, the evaporating nitrogen meant that convection was not negligible.

I made a few assumptions to simplify the model. The area between the LN<sub>2</sub> and the cap was assumed to be pure, ideal, and uncirculating nitrogen gas. At this stage, thermal contacts were assumed to be bonded. The delrin supports were also assumed to have negligible heat transfer. 

CONVECTION EQUATIONS AND AMBIENT TEMPERATURE PROFILES

Because the nitrogen gas was assumed to be still, I used natural convection equations found in my heat transfer textbook to estimate convection coefficient for each body in the system. At this point, I also moved the thermocouples to hang at various heights throughout the gaseous nitrogen. This gave me an estimate of the ambient temperature profile as a function of distance from the LN<sub>2</sub> surface (T<sub>inf</sub>). A combination of measured data and tabular values allowed me to estimate the convection coefficients on the relatively simple geometry.

ANSYS THERMAL SS AND TRANSIENT COOLDOWN

Overall the new model has much stronger correlation with the experimental data. It accurately captured the transient cooldown and was within ~3K during the steady state portion. There are many areas to improve here is what I thought would be most significant: <br>

1. Modeling of changing LN<sub>2</sub> level: I think this is the biggest source of error. In the experimental data, the "steady state" varies by several degrees as the LN<sub>2</sub> evaporates. I think I could've taken more experimental data and made the 77K LN<sub>2</sub> boundary condition a parameter in the simulation that varies over time to more accurately capture the steady state. <br>
2. More accurate fill level: Even when used in the lab, the LN<sub>2</sub> is just filled to a Kapton tape line in the dewar. This is a big source of variation between trials. <br>
3. Bonded thermal contact assumption: Clamping indium between copper is a very strong thermal conductor, but I still think that there is non-negligible contact resistance here. This is a value that could be measured or tweaked in the model to get a more accurate simulation. <br>

Regardless, the end user was satisfied with the results he was seeing after the small improvements that were made. My model provides a baseline for future changes and similar projects. This project was my first exposure to thermal modeling in ANSYS. I found the combination of experimental data collection, hand calculations, and simulation rewarding and hope to work on similar projects in the future.
