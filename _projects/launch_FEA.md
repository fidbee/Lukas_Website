---
layout: page
title:  FEA of an Apogee Control System
description: Structural analysis of airbrakes system during various stages of flight
img: assets/img/projects/launch/just_airbrakes.jpg
importance: 2
category: RIT Competetive Rocketry Team
giscus_comments: false
---

See "Mechanical Design of an Apogee Control System" project for an overview of the mechanism.

To verify the structural integrity of the airbrakes control system, FEA was performed for two different load cases: maximum extension and boost.

FEA SETUP DURING MAX EXTENSION

This setup essentially has every force at its worst case scenario. The leaftlets are extended all the way out, the servo is pushing with its maximum torque, and the springs are fully extended. The system is constrained by the bulkhead epoxied in place on our booster tube. The bearings were modeled as generic joints with the appropriate degrees of freedom constrained/free.

BEAM ELEMENT HARDWARE IMAGE

The system's hardware was simulated as 1D beam elements, with material and diameter of the bolt assigned to each element. Given the slender aspect ratio of the bolts, this is an adequate assumption for our applications. This significantly reduced computation time compared to the fine mesh and contacts needed when simulating an entire bolt and allowed for faster design iteration. The force vectors at each end of the 1D beam element were probed and exported in tabular format. These were then put into a spreadsheet that estimated the stress in each bolt with a couple of hand calculations. Given the massive factors of safety seen on these bolts (>20), it wasn't necessary to simulate the complete hardware.

BOLT AND BEARING AREA HAND CALCULATIONS

The above equations were used to estimate tensile and shear stress in the bolts based on the force results given by ANSYS. The maximum shear stress (σ<sub>s</sub>) was estimated to be 0.577 * maximum tensile stress (σ<sub>t</sub>) based on an approximation from Shigley's Mechanical Engineering Design. The shear and tensile stress were compared to these values to obtain a factor of safety (FOS). The bearing area stress was also calculated by probing each bearing joint and using hand calculations shown above. Overall, the FOS on all of the hardware was far above the require FOS of 3.

FEA RESULTS

The Von-Mises stress was analyzed for every other component and compared to the appropriate yield stress to obtain a FOS. There are expected stress concentrations at some of the sharp corners and the locations of maximum stress match intuition. Components with specified load ratings (such as the rails and carriages) were analyzed using those instead. Overall, after a few tweaks, every component in the system met the required FOS of 3.

LOAD CASE OF BOOST

The second load case was much simpler than the first. The rocket experiences about 15Gs of acceleration during boost. Given the small mass of all of the components in our system, the forces here were fairly small and all easily within our FOS.

FEA BOOST RESULTS

