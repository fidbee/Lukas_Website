---
layout: page
title: Combination Lock Solver
description: I built a device to open combination locks.
img: assets/img/projects/combo_locks.jpg
importance: 1
category: Other
related_publications: false
---

Growing up, combination locks in our household would slowly pile up as their combinations were forgotten. Since high school, I had the idea of building a small machine to solve these and recover these locks. I applied to the Dick and St Jane Reeve Student Initiated Project fund at RIT and got selected to receive funding to complete this project.

While there are approaches to lock solving in which you can feel out the first two numbers and guess the last, I found these to be difficult and inconsistent. I wanted my device to open the lock with no user intervention. Originally, I thought that with 40 numbers, there would be 40<sup>3 (64,000) combinations. Luckily this isn't the case. Because of machining tolerance and other factors, there are actually only 4,000 possible combinations for Masterlocks. There's even about a +/-1 window for hitting the correct number when you solve. This made brute forcing every combination a viable approach

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/wall_completed.jpg" title="wall_completed" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    This shows the device working for the first time. This run took about 20 minutes to solve, but it could take up to ~40 if you're unlucky.
</div>

THe design of the mechanism was not too complicated. A stepper motor (w/ a # of steps that's a multiple of 40) provides very repeatable positional motion. I used an electric solenoid to pull the shackle after each attempt and an IR beam break sensor would trip if it ever got opened. Interfacing with the lock was also surprisingly easy; it only took a few test 3D prints to get a firm connection that didn't slip. 

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/wall_completed.jpg" title="wall_completed" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    This shows the device working for the first time.
</div>

There were some interesting challenges when programming the mechanism. It turned out that my Arduino did not have enough storage to store all 4000 combinations of 3 numbers, even when taking steps to minimize how the data was stored. I instead had to generate and overwrite the sequence as it was solving. The approach I went with of locking in the first two numbers and then trying all 10 possible third numbers was effective given the circumstances. If I had a larger processor, I would like to try to find the optimal order to solve a lock to minimze the motion needed. Specifically, there are situations where you don't have to do a full 3 rotations to reset.


I'm still working on this project and there are three major areas for improvement. <br>
1. The solenoid + beam break sensor setup is very loud and clunky. I'm working on replacing this with just a single servo motor with feedback. By monitoring the current draw, I can tell when the lock is opened, or when a wrong combination was input. <br>