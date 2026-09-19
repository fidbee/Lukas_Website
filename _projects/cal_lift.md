---
layout: page
title: Calorimeter Lift Assist Mechanism
description: Created a device to assist in lifting a 35lb calorimeter
img: assets/img/projects/cal_lift/cal_thumbnail.png
importance: 3
category: Laboratory for Laser Energetics
---

An optical engineer in the beamlines group at the Laboratory for Laser Energetics (LLE) requested a mechanism to assist in the lifting of a 35lb calorimeter to ~5.5ft. Not only was this strenuous and challenging for some shorter operators, but the heat generated from a human carrying the calorimeter and lifting it actually let to some measurement inaccuracies (the added insulation mostly mitigated this). The customer asked for a passive assitance mechanism that would reduce the preceived weight to ~5lb. While this project did not involve any extensive analysis, the complexities with space constraints, safety, and accuracy made this a challenge.

IMAGE OF DIFFERENT ASSIST OPTIONS

I started by thinking about a few different ways to assist in lifting. All of were mocked up in CAD and I ended up choosing to use a constant force spring. This option had a very low profile and met all of the requirements.

PROTOTYPE

Having never worked with constant force springs before, I wanted to make a quick prototype as a proof of concept before the full design. A weaker spring was ordered and combined with an existing rail as well as some simple new parts. Two things were learned from this setup: <br>
1. The inner diameter of the spring changes as it unravels. This causes the spring to catch on the OD of the rod as it unravels. <br>
2. Allowing the rod to freely rotate provides much smoother motion that forcing the spring to slip along the rod. The rod was mounted on ball bearings for the final design.

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


GIFS OF LIFT ASSIST