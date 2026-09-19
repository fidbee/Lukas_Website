---
layout: page
title: Coupled Double Pendulum Simulation and Testing
description: Created a theoretical model of a double pendulum and compared to measured results
img: assets/img/projects/double_pend/double_pend_anim.png
importance: 3
category: Other
---

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/double_pend/pend_anim.gif" title="pend_anim" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Animation of double pendulum model
</div>

As part of one of my mechanical engineering courses I created a theoretical model of a coupled double pendulum. The predicted trajectory of this model was then compared to experimental data.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/double_pend/system_diagram.png" title="system_diagram" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Diagram of system
</div>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/double_pend/pend_fbds.png" title="pend_fbds" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Free body diagrams used to obtain acceleration expressions
</div>

I chose to use a mechanics (sum force & moments) approach to solve for the angular acceleration of each linkage. This results in 6 linearly independent expressions with 6 unknowns that can be solved for. While an energy based approach may have resulted in simpler expressions, I was using MATLAB to symbolically solve the resultant expressions. In the end, the 6x6 matrix of accelerations and reaction forces spit out the following monster expression for the angular acceleration of each link.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/double_pend/pend_expressions.jpg" title="pend_expressions" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Expressions for the angular acceleration of each link that were spit out by MATLAB. It's possible that some of this trig could be simplified in ways that MATLAB doesn't recognize.
</div>

Despite how complicated this looks, it did look about how you would expect when simulated. I used the ode45 numerical integration routine to calculate linkages positions over time given teh expressions for acceleration. Additionally, the energy of the system is conserved over time, which is a good sign. The simulated linkages were then compared to experimental results.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/double_pend/tracking.png" title="tracking" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    A tracking software called Kinovea was used to get the position of each link over time from a high speed video.
</div>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/double_pend/theo_vs_exp.png" title="theo_vs_exp" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    A comparison between experimental and simulated data
</div>

Overall the model had pretty good correlation with the experimental data. Error bars are generated theoretical data based on a Monte Carlo simulation where the uncertainty of each parameter (mass, lengths, starting angle, etc.) was taken into account. Experimental uncertainty was measured based on the standard deviation over multiple trials. The location of the second linkage especially deviates with the theoretical model over time. This is probably because of the frictionless bearing assumption in the model.