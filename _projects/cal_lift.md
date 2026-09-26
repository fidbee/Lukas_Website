---
layout: page
title: Calorimeter Lift Assist Mechanism
description: Created a device to assist in lifting a 35lb calorimeter
img: assets/img/projects/cal_lift/cal_irl.jpg
importance: 3
category: Laboratory for Laser Energetics
---

An optical engineer in the beamlines group at the Laboratory for Laser Energetics (LLE) requested a mechanism to assist in the lifting of a 35lb calorimeter to ~5.5ft. Not only was this strenuous and challenging for some shorter operators, but the heat generated from a human carrying the calorimeter and lifting it actually led to some measurement inaccuracies (the added insulation mostly mitigated this). The customer asked for a passive assistance mechanism that would reduce the perceived weight to ~5lb. While this project did not involve any extensive analysis, the complexities with space constraints, safety, and accuracy made this a challenge.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/cal_lift/lift_options.jpg" title="lift_options" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Lift assist options
</div>

I started by thinking about a few different ways to assist in lifting. All of were mocked up in CAD and tested for interference. Given all of the beams propagating in the area and walkways that had to remain clear, the space taken up was a big concern. I ended up choosing to use a constant force spring because of its low profile.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/cal_lift/cal_prototype_2.jpg" title="cal_prototype_2" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/cal_lift/cal_prototype_3.jpg" title="cal_prototype_3" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Prototype lift assist mechanism
</div>

Having never worked with constant force springs before, I wanted to make a quick prototype as a proof of concept before the full design. A weaker spring was ordered and combined with an existing rail as well as some simple new parts. Two things were learned from this setup: <br>
1. The inner diameter of the spring shrinks as it unravels. This causes the spring to catch on the OD of the rod as it unravels. <br>
2. Allowing the rod to freely rotate provides much smoother motion than forcing the spring to slip along the rod. I tested this by mounting the rod on shoulder bolts. In the final design, the rod was mounted on ball bearings.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/cal_lift/cal_design_1.jpg" title="cal_design_1" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Carriage and top of travel
</div>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/cal_lift/cal_design_2.jpg" title="cal_design_2" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Rails and spring assembly
</div>

The images above show some of the key features in the design. The two constant force springs are mounted on the fixed frame (orange). When the calorimeter is lowered, the extended springs are encased within C channel as a protection mechanism for the stored energy if it were to somehow be released. An enclosure also covers the top of the springs for the same reason. Two quick release pins hold the carriage at the top of its travel and provide an extra safety measure at the bottom of travel. The entire carriage slides along two ball bearing rails. At the top of travel, the entire top plate of the carriage can rotate on "magic" washers to match the orientation of the nest that it slides onto. PTFE pads underneath the sliding components make the sliding motion smooth and unlikely to catch on anything. As mentioned in the prototype images, the constant force springs roll along a set of ball bearings for smoother motion. Various lightweighting pockets were placed in the carriage to achieve the proper force balance.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/cal_lift/cal_lowered.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/cal_lift/cal_raised.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/cal_lift/cal_in_use.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

The images above show the three stages of use for the lift assist mechanism. Most of the time, it's stored in its downward position. When used, it's raised along the rails, pushed into place, and aligned to the beam. 

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/cal_lift/cal_up.gif" title="cal_up" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/cal_lift/cal_down.gif" title="cal_down" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Installed lift assist being raised and lowered (sped up)
</div>

After a few weeks in the manufacturing queue, the mechanism was machined and installed. A few quality of life changes were made, such as mitigating a pinching hazard and making the lift handle larger. Overall, the design was met with positive feedback from the users. Through this project, I learned about proper press fit tolerancing, customer communication, and safe design. I also got a lot more comfortable with drafting efficiently with GD&T due to the dozens of custom parts in this project.