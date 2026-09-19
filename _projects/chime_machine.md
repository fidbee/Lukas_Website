---
layout: page
title: Automatic Chime Machine
description: Designed, programmed, and constructed an automatic chime machine
img: assets/img/projects/chime_machine/chime_machine.jpg
importance: 4
category: Other
---

In one of my first year engineering courses, I worked with a group of 3 other students to create a chime machine. We chose to play the song "Little Talks" by Of Monsters and Men because of the relatively simple chorus. I ended up doing a lot of the electronics and programming for this project and got introduced to Arduino control. I even wrote a script to convert sheet music into a text file format that could be used by the Arduino. 

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/chime_machine/chime_machine.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Completed chime machine
</div>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/chime_machine/chimes_animation.gif" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Animation of chime machine
</div>

A laser cut frame suspended our seven chimes above a series of solenoids. For simplicity, we wanted as many chimes as possible to be struck by solenoids instead of motors. One interesting problem was that because the magnetic solenoids pull down when actuated, turning the solenoid off is actually what strikes the chime. A spring was used to basically reverse the orientation. However, because the default state was on, our solenoids got very hot and ended up melting some of the dampers on them. This meant that we could really only run our chime machine for about 2 minutes before it started to smell bad.