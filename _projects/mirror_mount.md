---
layout: page
title: Analysis of a 3DOF Mirror Mount
description: ANSYS and Sigfit were used to predict surface deformations
img: assets/img/projects/mirror_mount_full.png
importance: 1
category: Laboratory for Laser Energetics
related_publications: false
---

During my last block at the Laboratory for Laser Energetics, I was tasked with the design and analysis of a 3DOF mirror mount for a lightweight, off-axis, elliptical, THz mirror. Upstream optics could control another 2DOF. While the design of the mirror itself was mostly fixed in the state a previous employee left it in, I had a lot of freedom in how I could accurately hold and manipulate this experimental mirror. 

FLEXURE THRU CG
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/5.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    This image can also have a caption. It's like magic.
</div>

I decided to go with a rod flexure based design to hold the back of the mirror. The six thin flexures act as single force members to constrain the six degrees of freedom and avoid overconstraint. Because of the flexibility of the flexures, small locational innacuracies in mounting points do not cause significant deformation of the optical surface. Inspiration for this design and some of the corresponding analysis came from: (BLUE BOOK)

ANSYS IMAGES
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

To determine flexure material, dimensions and mounting locations, I ran several parametric studies in ANSYS + Sigfit. In this case, I was looking at the surface deformation due to 1g lateral gravity sag. I exported ANSYS nodal results to a program called Sigfit to subtract rigid body motion and isolate the deformation on the optical surface. Surface RMS was used as a metric to compare different combinations of parameters for optical performance. By simulating dozens of combinations of radial mount spacing, flexure material, and flexure diameter, I arrived at a design that minimized surface deformation while still adequately supporting the mirror. 

BEAM ELEMENT FLEXURES AND SIGFIT RESULTS

The 3DOF positioning mechanism was designed in a similar fashion to the flexured back of the mirror. 