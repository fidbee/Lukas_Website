---
layout: page
title:  Mechanical Design of Apogee Control Mechanism
description: Hand calculations, modeling, and testing
img: assets/img/projects/launch/just_airbrakes.jpg
importance: 1
category: RIT Competetive Rocketry Team
giscus_comments: false
---

As part of the IREC competetive rocketry competition, one of the things that will earn you the most points is getting as close as possible to your target apogee. The team at RIT competes in the 10k COTS category, meaning that we target an apogee of 10,000 feet. For the 2025-26 rocket, the team attempted to add an active apogee control mechanism to the rocket for the first time. The plan was to select a motor that would intentionally overshoot the apogee target and adjust the drag of the rocket after boost to hit the apogee just right.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/launch/airbrakes_diagram.jpg" title="airbrakes_diagram" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    An overview of the airbrakes system
</div>

The two leaflets shown above extend outside of the 6"Ø rocket to provide an increased drag force. A central servo rotates a two bar linkage to extend the mechanism. The curved shape of the linkages allows them to collapse in on themselves to save space.Threaded bearings connect the linkages to each other. Two springs provide a mechanical failsafe such that the system  retracts to a neutral state if power is lost or an abort signal is received. The leaflets slide on two ball bearing carriages and rails. The leaflets were sized based on a balance of required control authority and tube strength given the large cutouts to accomodate them.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/launch/linkage_calculations.jpg" title="linkage_calculations" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Hand calculations relating torque to applied force in a two bar linkage
</div>

The two bar linkage system shown above was simulated in order to select an appropriate servo and spring. Based on the free body diagrams above and some trig, an expression for the required servo torque was derived. A few parameters had to be estimated to predict the appropriate drag force. The plate drag coefficient (C<sub>d</sub>) was predicted using a combination of hand calculations, CFD, and experimental data. This number was a point of debate and varied greatly between methods, making it a large source of error. A factor of safety of 3 helped combat these innacuracies. In future iterations of the design, more extensive CFD will try to get a more accurate estimate. Rocket velocity after boost is estimated from OpenRocket simulations and the friction coefficient of the rails was measured experimentally.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/launch/rail_friction.png" title="rail_friction" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    The friction of the rails and carriages was measured experimentally using a force gauge. (I was dressed as Tyler Durden for a Halloween costume here...)
</div>

<div class="row justify-content-sm-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/launch/all_triangles.jpg" title="all_triangles" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/launch/d1_d2_linkages.jpg" title="d1_d2_linkages" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Left: Visualization of every linkage combination and mounting point simulated. The white space on the right is due to the ommission of combinations that approach infinite torque requirements. <br>
    Right: Torque required at each combination of linkage length. There's a third dimension to this representing the mounting point location on the leaflet (d3) but it's not shown for visual clutter. The red dot represents the linkage dimensions chosen for the least torque. The right side of the graph is empty due to those dimensions not fitting within the rocket. The left side is omitted due to the torque approaching infinity in this region.
</div>

With an equation to relate the drag of the leaflets to the required servo torque, I wrote a MATLAB script to simulate every possible linkage configuration that fits within the rocket tube and meets the required extension distance. Configurations with an angle between the linkages (θ<sub>2</sub>) near 90° were removed due to their required torque approching infinity. More geometry constraints will be implemented as components are selected and changed. Everything was looked at in the highest force scenario of the rocket immediately exiting the boost phase and extending the leaflets to their maximum. With this script, the optimal linkage dimensions and starting angle to minimize servo torque were obtained. This linkage optimization was done for the improved 2026-27 design, and reduced the required servo torque by about half! Overall, the linkage geometry selected in 2025-26 was somewhat arbitrary and resulted in a significantly overspecced servo. The spring constant was selected by running the script without a spring, and speccing the minimum COTS spring that provided at least enough force to overcome this force without a spring.

<div class="row justify-content-sm-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/launch/risk_launch.png" title="risk_launch" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/launch/airbrakes_and_electronics.jpg" title="airbrakes_and_electronics" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Left: Our 2025-26 rocket "RISK" being launched! <br>
    Right: Airbrakes system integrated into the rocket tube during a test flight
</div>


Overall, the mechanical design of the 2025-26 apogee control system worked very well. However, there are a couple of areas for improvement for the 2026-27 system.<br>

1. The countersunk screws connecting the leaflets to the carriages overconstrain the carriages and resulted in poor assembly. Changing these to regular clearance holes will make them non-locating features to mitigate this. <br>

2. The aforementioned linkage optimization will reduced the required servo torque and save us some money and space. <br>

3. Reduction in FOD: The rails and carriages were nearly impossible to move after recovery of the rocket due to the ammount of FOD build up. While this likely accumulated after the flight, adding a smaller rubber seal around the leaflet holes in the tube will help mitigate this. <br>

4. Ease of assembly: A couple of screws were difficult to access and the springs proved to be a pain to assembly. Ease of assembly will be consider more moving forward. <br>

5. The springs will likely to switched to a single torsion spring. This has a much smaller footprint and won't need to be reassembled every time the system is maintenanced. <br>