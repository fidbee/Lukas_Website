---
layout: page
title: Combination Lock Solver
description: I built a device to open combination locks.
img: assets/img/projects/combo_lock/combo_locks.jpg
importance: 1
category: Other
related_publications: false
---

Growing up, combination locks in our household would slowly pile up as their combinations were forgotten. Since high school, I had the idea of building a small machine to solve these and recover these locks. I applied to the Dick and St Jane Reeve Student Initiated Project fund at RIT and got selected to receive funding to complete this project.

While there are approaches to lock solving in which you can feel out the first two numbers and guess the last, I found these to be difficult and inconsistent. I wanted my device to open the lock with no user intervention. Originally, I thought that with 40 numbers, there would be 40<sup>3</sup> (64,000) combinations. Luckily this isn't the case. Because of machining tolerance and other factors, there are actually only 4,000 possible combinations for Masterlocks. There's even about a +/-1 window for hitting the correct number when you solve. This made brute forcing every combination a viable approach

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include video.liquid path="https://www.youtube.com/watch?v=Nxkj5G0dqsM" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    This shows the device working for the first time. This run took about 20 minutes to solve, but it could take up to ~40 if you're unlucky.
</div>

THe design of the mechanism was not too complicated. A stepper motor (w/ a # of steps that's a multiple of 40) provides very repeatable and fast positional motion. I measured the force needed to open the lock and used an electric solenoid to pull the shackle after each attempt. The original idea of simply applying a constant force on the shackle the whole time didn't work because the lock would jam. An IR beam break sensor was tripped if the lock ever got opened. Interfacing with the lock was also surprisingly easy; it only took a few test 3D prints to get a firm connection that didn't slip. One side interfaces with a modified pulley spline and the other on the lock.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/combo_lock/solving_order.jpg" title="solving_order" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Current approach to attempting combhinations.
</div>

There were some interesting challenges when programming the mechanism. It turned out that my Arduino did not have enough storage to store all 4000 combinations of 3 numbers, even when taking steps to minimize how the data was stored. I instead had to generate and overwrite the sequence as it was solving. The approach I went with of locking in the first two numbers and then trying all 10 possible third numbers was effective given the circumstances. If I had a larger processor, I would like to try to find the optimal order to solve a lock to minimze the motion needed. Specifically, there are situations where you don't have to do a full 3 rotations to reset.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/combo_lock/solenoid_to_servo.jpg" title="solenoid_to_servo" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    I'm working on replacing the solenoid with a servo.
</div>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/combo_lock/breadboard_to_pcb.jpg" title="breadboard_to_pcb" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    I'm designing my first PCB to make the device more compact.
</div>

I've recovered the combinations of all the locks I have sitting around, but I'm still working on this project. There are two major areas for improvement. <br>
1. The solenoid + beam break sensor setup is very loud and clunky. I'm working on replacing this with just a single servo motor with feedback. By monitoring the current draw, I can tell when the lock is opened, or when a wrong combination was input. <br>
2. I want to make this device portable and able to be used on a lock that's attached to something. I've begun the design of a custom PCB to fit the device in the enclosure I modeled. Having never made a PCB before, this has been challengeing but nevertheless a good learning experience. I'm also adding an LCD display to show current progress and attempts.