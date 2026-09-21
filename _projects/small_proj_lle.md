---
layout: page
title: Various Smaller Projects
description: Shorter term projects I worked on
img: assets/img/projects/cal_lift/cal_thumbnail.png
importance: 4
category: Laboratory for Laser Energetics
---

An optical engineer reported some issues with an existing lens assembly design and wanted me to fix them before manufacturing. The lens setup is used in a vacuum chamber at LLE to study high powered pulsed lasers. The design was to be modified to accomodate both 6" and 5.91" (150mm) optics. Additionally, there was unwanted contact between metal and optical components that required some redesign.

IMAGE OF DESIGN

A small delrin ring (blue) was added to a modified alumnimum retaining ring (red). This ensured that the only contact with the optic was on the delrin mounting points. The ring has a slight clearance fit and is secured by a couple of small screws. I thought about cooling the ring down and giving it a shrink fit but decided this wasn't worth it. A locating mechanism with 3 delrin pins pins was designed to hold the optic in place. These pins could then be shifted to adjacent holes when the other optic size needs to be used. I thought this was a pretty elegant solution that was possible because of how close in diameter the two optics are. The retaining ring (red) clamping mechanism of the previous design was kept.

This was one of my first projects at LLE and I learned a lot from it. I learned how to properly calculate the tolerance stackup on the locating pins to ensure that the lens had the required positional accuracy. Because this assembly is used under vacuum in a clearnroom, I learned the basics of vacuum compatible design. 

LIFT ASSIST IMAGE

Another project I worked on was a new lift assit mechanism for a 60lb X-RAY camera. This camera is used to measure X-RAY scattering off of the back fusion targets after they are struck by the laser. The existing rigging fixture had a pretty major flaw: quick release pins were used to secure the rigging fixture. Since the camera has to be held at several extreme angles, the pins are increasingly axially loaded, something they're not designed or rated for. This is seen clearly in the image above. The original design culminated in an incedent at the lab where some equipment was damaged. My task was to redesign the rigging fixture to mitigate this. 

CONCEPTS

I presented a few concepts to the stakeholders. Unfortunately, this was not as simple as just replacing the quick release pins with screws (#1) because the mating part could not be modified. Changing the orientation of the pins to always be in shear (#2) ended up not working within the space constraints. Quarter turn fasteners (#4) were a cool idea because of how easy they are to engage/disengage but ended up not working with space constraints and load ratings. I ended up going with concept #3, where the side rails are modified to accomodate captives screws. While this isn't as convenient as quick release pins, it is far more secure. The lift bar was also modified to include rigging holes that will have the camera rest at 1 of 8 different angles depending on which of the 8 potential locations it needs to be used in. I measured the CG of the camera (matched CAD) to get the location of these holes.

ANSYS SETUP

To properly select component dimensions and bolt sizes, the assembly was simulated in ANSYS. A load rating of 125lbs (1.25 FOS on max load) was used. The setup was pretty straightforward, with only 1 force applied. The complexity came more in properly model the various bolted connections. Initially, every possible lift bar angle was tested, but, as expected, the most extreme loading angles provided the highest stress. While making changes to the design, only these load cases were looked at for simplicity. 

ANSYS RESULTS

The ANSYS structural simulations showed that in the two most extreme load cases, the aluminum components were all well within their yielding FOS. A custom bolt calculator created by the lab was used for all bolted connections. In ANSYS, beam elements were used to simulate the bolt, and the force vectors probed at each end are input into the calculator. I used a similar approach to this for FEA on RIT's competetive rocketry team (see [FEA of an Apogee Control System](/projects/launch_MECE_design)). The image above shows an example of some of the inputs and outputs I generated here. The relatively low factor of safety requirements are because of the preload in the connection, which brings the bolt already to 75% of its yield stress. This is simulated using the built in preload tool in ANSYS. Overall, every component met its factor of safety and my design was implemented, machined, and received overall positive feedback from the users.

Through this project, I learned a ton about what goes into a bolted connection. The lab's bolt calculator as well as some of the provided documentation were very informative. I even got the chance to add some more capabilities to the calculator to estimate how moment loads on a bolt can impact its strength. I also got much more comfortable with ANSYS mechanical and learned about several methods of hardware modeling within the program.

