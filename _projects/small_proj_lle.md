---
layout: page
title: Various Smaller Projects
description: Shorter term projects I worked on
img: assets/img/projects/misc_lle/old_rigging_fixture.jpg
importance: 4
category: Laboratory for Laser Energetics
---

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/misc_lle/lens_asm_overview.jpg" title="lens_asm_overview" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Overview of lens assembly design
</div>

An optical engineer reported some issues with an existing lens assembly design and wanted me to fix them before manufacturing. The lens setup is used in a vacuum chamber at LLE to study high powered pulsed lasers. The design was to be modified to accommodate both 6" and 5.91" (150mm) optics. Additionally, there was unwanted contact between metal and optical components that required some redesign.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/misc_lle/lens_asm_design.jpg" title="lens_asm_design" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    All points of aluminum on optic contact were removed and replaced with delrin. 
</div>

A small delrin ring (blue) was added to a modified aluminum retaining ring (red). This ensured that the only contact with the optic was on the delrin mounting points. The ring has a slight clearance fit and is secured by a few small screws. I thought about cooling the ring down and giving it a shrink fit but decided this wasn't worth it. A locating mechanism with 3 delrin pins was designed to hold the optic in place. These pins could then be shifted to adjacent holes when the other optic size needs to be used. I thought this was a pretty elegant solution that was possible because of how close in diameter the two optics are. The retaining ring (red) clamping mechanism of the previous design was kept.

This was one of my first projects at LLE and I learned a lot from it. I learned how to properly calculate the tolerance stackup on the locating pins to ensure that the lens had the required positional accuracy. Because this assembly is used under vacuum in a cleanroom, I learned the basics of vacuum compatible design. 

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/misc_lle/lift_bar_existing_setup.jpg" title="lift_bar_existing_setup" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    The existing rigging setup for the lift bar. This was a lab test with a 100lb weight to show why the quick release pin design was an issue.
</div>

Another project I worked on was a new lift assist mechanism for a 60lb X-ray camera. This camera is used to measure X-ray scattering off of the back fusion targets after they are struck by the laser. The existing rigging fixture had a pretty major flaw: quick release pins were used to secure the rigging fixture. Since the camera has to be held at several extreme angles, the pins are increasingly axially loaded, something they're not designed or rated for. The load is placed entirely on the detent balls in this case. This is seen clearly in the image above. The original design culminated in an incident at the lab where some equipment was damaged. My task was to redesign the rigging fixture to mitigate this. 

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/misc_lle/lift_bar_concepts.jpg" title="lift_bar_concepts" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    A couple of concepts I explored for the lift bar
</div>

I presented a few concepts to the stakeholders. Unfortunately, this was not as simple as just replacing the quick release pins with screws (#1) because the mating part could not be modified. Changing the orientation of the pins to always be in shear (#2) ended up not working within the space constraints. Quarter turn fasteners (#4) were a cool idea because of how easy they are to engage/disengage but ended up not working with space constraints and load ratings. I ended up going with concept #3, where the side rails are modified to accommodate captive screws. While this isn't as convenient as quick release pins, it is far more secure. The lift bar was also modified to include rigging holes that will have the camera rest at 1 of 8 different angles depending on which of the 8 potential locations it needs to be used in. I measured the CG of the camera (matched CAD) to get the location of these holes.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/misc_lle/lift_bar_setup.jpg" title="lift_bar_setup" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Lift bar ANSYS setup
</div>

To properly select component dimensions and bolt sizes, the assembly was simulated in ANSYS. The imum load of 100lbf was used. The setup was pretty straightforward, with only 1 force applied. The complexity came more from properly modeling the various bolted connections. Initially, every possible lift bar angle was tested, but, as expected, the most extreme loading angles provided the highest stress. While making changes to the design, only these load cases were looked at for simplicity. 

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/misc_lle/lift_bar_ansys_results.jpg" title="lift_bar_ansys_results" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Some results of component stresses on the lift bar
</div>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/misc_lle/lift_bar_bolt_results.jpg" title="lift_bar_bolt_results" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Results of bolt calculations on lift bar
</div>

The ANSYS structural simulations showed that in the two most extreme load cases, the aluminum components were all well within their yielding FOS. A custom bolt calculator created by the lab was used for all bolted connections. In ANSYS, beam elements were used to simulate the bolt, and the force vectors probed at each end were input into the calculator. I used a similar approach to this for FEA on RIT's competitive rocketry team (see [FEA of an Apogee Control System](/projects/launch_FEA)). The image above shows an example of some of the inputs and outputs I generated here. The relatively low factor of safety requirements are because of the preload in the connection, which brings the bolt already to 75% of its yield stress. This is simulated using the built in preload tool in ANSYS. Overall, every component met its factor of safety and my design was implemented, machined, and received overall positive feedback from the users.

Through this project, I learned a ton about what goes into a bolted connection. The lab's bolt calculator as well as some of the provided documentation were very informative. I even got the chance to add some more capabilities to the calculator to estimate how moment loads on a bolt can impact its strength. I also got much more comfortable with ANSYS mechanical and learned about several methods of hardware modeling within the program.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/misc_lle/detrit_overview.jpg" title="detrit_overview" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Overview of the nitrogen bubbling tank
</div>

For one of my earlier projects at the lab, I designed the tank pictured in the image here. In short, the Tritium Science group requested a device to bubble nitrogen gas through a bath of water and output a combination of water vapor and nitrogen ("wet nitrogen"). This is used upstream for various experiments relating to removing tritium contamination from water. Tritium is used as a fuel source during the fusion reactions performed at the lab.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/misc_lle/detrit_batch_can.jpg" title="detrit_batch_can" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    The original batch can design I was thinking about using for this project. Hand calculations and ANSYS showed that this would've been a poor choice.
</div>

I originally looked at modifying a batch can to include passthroughs for our inlet and outlet. While the system is not supposed to operate at high pressure (<4psi), the batch cans did not have any specified pressure ratings. Some simple hand calculations of a flat plate with uniform pressure showed that the can would yield under just a couple of psi. This was verified in ANSYS. 

I instead went with the slightly more expensive but much simpler ASME rated pressure vessel seen in the first images. This already had inlet and outlets incorporated in the lid and was rated for pressures far above those expected in our application. After selecting a few tubing components, an appropriately sized sparger, and a pressure relief valve, the design was completed and parts were procured. The lab users reported good results using the new setup.