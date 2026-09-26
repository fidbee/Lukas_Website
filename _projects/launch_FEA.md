---
layout: page
title: FEA of an Apogee Control Mechanism
description: Structural analysis of airbrakes system during various stages of flight
img: assets/img/projects/launch/fea_thumbnail.png
importance: 2
category: RIT Competitive Rocketry Team
giscus_comments: false
---

See "[Mechanical Design of Apogee Control Mechanism](/projects/launch_MECE_design)" project for an overview of the mechanism being analyzed.

To verify the structural integrity of the airbrakes control system, FEA was performed for two load cases: maximum extension and boost.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/launch/max_extension_setup.jpg" title="max_extension_setup" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    FEA setup during the maximum extension load case
</div>

This setup essentially has every force at its worst case scenario. The leaflets are extended all the way out, the servo is pushing with its maximum torque, and the springs are fully extended. The system is constrained by the bulkhead epoxied in place on the booster tube. The carriage extension is constrained by two delrin hard stops (not seen here). The bearings were modeled as generic joints with the appropriate degrees of freedom constrained/free.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/launch/beam_element_setup.png" title="beam_element_setup" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Example showing how 1D beam elements are scoped (not directly from this simulation)
</div>

The system's hardware was simulated as 1D beam elements, with material and diameter of the bolt assigned to each element. Given the slender aspect ratio of the bolts, this is an adequate assumption for our applications. This significantly reduced computation time compared to the fine mesh and contacts needed when simulating an entire bolt and allowed for faster design iteration. The force vectors at each end of the 1D beam element were probed and exported in tabular format. These were then put into a spreadsheet that estimated the stress in each bolt with a couple of hand calculations. Given the massive factors of safety seen on these bolts (>20), it wasn't necessary to mesh and simulate the bolts in full.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/launch/bolt_hand_calcs.jpg" title="bolt_hand_calcs" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Hand calculations used to estimate the FOS of our hardware
</div>

The above equations were used to estimate tensile and shear stress in the bolts based on the force results given by ANSYS. The maximum shear stress (σ<sub>s</sub>) was estimated to be 0.577 * maximum tensile stress (σ<sub>t</sub>) based on an approximation from [Shigley's Mechanical Engineering Design](https://www.mheducation.com/highered/product/shigleys-mechanical-engineering-design-nisbett.html?viewOption=student). The shear and tensile stress were compared to these values to obtain a factor of safety (FOS). The bearing area stress was also calculated by probing each bearing joint and using hand calculations shown above. Overall, the FOS on all of the hardware was far above the required FOS of 3.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/launch/fea_extension_results.jpg" title="fea_extension_results" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Some of the component stresses during the maximum extension load case. Every component was looked at but only four are shown here.
</div>

The Von-Mises stress was analyzed for every other component and compared to the appropriate yield stress to obtain a FOS. There are expected stress concentrations at some of the sharp corners and the locations of maximum stress match intuition. Components with specified load ratings (such as the rails and carriages) were analyzed using those instead. Overall, after a few tweaks, every component in the system met the required FOS of 3.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/launch/fea_boost_setup.jpg" title="fea_boost_setup" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Setup for the ~15Gs experienced during boost
</div>

The second load case was much simpler than the first. The rocket experiences about 15Gs of acceleration during boost. Given the small mass of all of the components in our system, the forces here were fairly small and all easily within our FOS.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/launch/fea_boost_results.jpg" title="fea_boost_results" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Stresses are very low during the boost phase
</div>

