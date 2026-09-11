---
layout: page
title: Analysis of a 3DOF Mirror Mount
description: ANSYS and Sigfit were used to predict surface deformations
img: assets/img/projects/mirror_mount_full.png
importance: 1
category: Laboratory for Laser Energetics
related_publications: false
---

During my last block at the Laboratory for Laser Energetics, I was tasked with the design and analysis of a 3DOF mirror mount for a lightweight, off-axis, elliptical, THz mirror. Upstream optics could control another 2DOF. While the design of the mirror itself was mostly fixed in the state a previous employee left it in, I had a lot of freedom in how I could accurately hold and manipulate this experimental mirror. Inspiration for this design and some of the corresponding analysis came from: (BLUE BOOK). Feel free to email me for any questions and more detailed presentations.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/mirror_mount/flexure_thru_CG.jpg" title="flexure_thru_CG" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    The virtual intersection point of each flexure pair intersects with the plane of the CG to minimize moment loads in the mirror.
</div>

I decided to go with a bipod rod flexure based design to hold the back of the mirror. The six thin flexures act as single force members to constrain the six degrees of freedom and avoid overconstraint. Because of the flexibility of the flexures, small locational innacuracies in mounting points do not cause significant deformation of the optical surface. One end of each flexure is threaded into the mirror while the other is epoxied in place at its mounting point. A custom fixture was developed to hold the mirror in its neutral state while the epoxy cured. This minimized any pre-stress that might be imposed on the mirror during assembly. 

ANSYS IMAGES
BEAM ELEMENT FLEXURES AND SIGFIT RESULTS
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

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/mirror_mount/annotated_mirror_mount.jpg" title="annotated_mirror_mount" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    The full design of the mirror. The yellow rod flexures constrain the mirror to only move in the desired DOF controlled by the actuators (tip, tilt, piston).
</div>

Instead of a traiditional cone, vee, flat kinematic mount, I again went with a flexure mechanism (which constrains the same degrees of freedom). This eliminates the lateral load placed on the actuators and instead places the weight of the mirror on the flexures. Because the actuators push on three flats, this design also minimizes the contact friction of the rotating actuators on their kinematic nests. This approach has downsides of locational accuracy and repeatability, but, given the experimental nature of this design, it was an appropriate choice. I used a similar parameter-based simulation to determine the dimensions and material of these flexures. The manual actuators allow for ~10mm piston, and ~±2.25° tip/tilt at 0.143°/rev resolution. The buckling strength of each flexure was verified with hand calculations.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/mirror_mount/surface_def_workflow.jpg" title="surface_def_workflow" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    The general workflow I used in this project.
</div>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/mirror_mount/raytracing_results.jpg" title="raytracing_results" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    OSLO raytracing results of the mirror deformed under 1g lateral sag at a 6THz frequency.
</div>

The design of the entire assembly was looked at in a variety of load cases. The nodal results from ANSYS were again exported to Sigfit to remove rigid body motion. The deformed optic was then run through a raytracing simulation in OSLO at a variety of wavelengths to determine at what point diffraction limited performance is achieved. The example above shows the simulated performance of the mirror under 1g lateral sag. At the expected 6THz (λ = 50µm) frequency, the performance of the mirror is diffraction limitted. Nevertheless, machining and other error accumulation will certainly change the wavelength at which performance is diffraction limited. Vibrational and thermal anlyses were also conducted at this stage.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/mirror_mount/all_disturbances.jpg" title="all_disturbances" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Different disturbances were applied to each mounting point to simulate the flatness of the mounting components. Rotation about the X axis has by far the largest impact. This is expected when considering the geometry of the flexures and the axes in which it is stiff and flexible.
</div>

The sensitivity of dimensions on the flexured mount were analyzed using ANSYS + Sigfit Monte Carlo toolbox. Small displacements were applied to each mounting point and the impact on the optical surface was analyzed. Because the displacements at this scale were assumed to be linear, different combinations of mounting point error can be summed to determine their combined effect. Sigfit automates this process and can provide several performance metrics.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/mirror_mount/surface_deformation_animation.gif" title="surface_deformation_animation" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Animation showing the simulated optical surface through a range of coplanarity (displacement in z) values. A normal distribution of thousands of these deformations were generated and summed to obtain Monte Carlo results.
</div>

A normal distribution was assumed for each displacement and thousands of different combinations of displacements were summed. The optical surface RMS was then extracted from each simulation and graphed below. This shows us the probability that a certain surface RMS can be achieved based on the flatness and locational tolerance of the flexure mounting points. It shows that the flexured design is behaving as expected; where small locational innacuracies do not contribute significantly to surface deformation. As a point of comparison, I ran the same simulation except without the flexures. This is akin to just bolting a rigid plate to the back of the mirror. As expected, the surface deformations are orders of magnitude higher if you were to go with this approach.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/mirror_mount/RMS_probability.jpg" title="RMS_probability" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    The probability that a given surface RMS can be achieved given an input set of disturbances. Blue represents the flexure based design while orange represents a rigid plate bolted to the back of the mirror. The tens of microns RMS with the rigid plate would not be acceptable while the sub-micron accuracy of the flexures is acceptable at this wavelength. Note the log scale.
</div>

Overall this was my favorite project I had the chance to work on at LLE. I greatly expanded my knowledge of FEA techniques and how they can be combined with optical software to translate between mechanical and optical requirements. While there are certainly things I would do differently if I were starting from scratch, I'm happy with how the design turned out and excited to get an update on its performance once manufacturing and assembly are complete.
