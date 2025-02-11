---
title: "Gnome Gnolf"
date: 2024-08-30
---
![A smartphone shows an augmented reality application in which a putter is attached to the phone and a minigolf course floats in front of the phone. On the left of the course is the ball, around which is a yellow circle. A gnome stands nearby, along with several mushrooms. A sloped curve leads to the right side of the course, where the hole is blocked off by a stone wall and a wooden triangular prism.](/assets/images/gnome-gnolf-header.png)

# Overview
Gnome Gnolf is a game I worked on with The MIT Scheller Teacher Education Program and The Education Arcade. This game is part of a study researching how to effectively design an augmented reality (AR) game to provide an introduction to a subject and increase players' positive affect towards it. In particular, Gnome Gnolf seeks to do this with geometry by building a game around [rigid transformations](https://en.wikipedia.org/wiki/Rigid_transformation){:target="_blank"} (translation, rotation, and reflection) to be played on a phone. This study is still ongoing as of the writing of this post. Over the course of the game, the player must use their putter and the gnomes together to navigate a minigolf-style course.

# My Role
I worked in several roles over the course of this project. Over summer 2021, I worked on the design team, fleshing out the core mechanics of the game and designing several of the holes of the gnolf course; the design team also received weekly builds from the programming team, and  we tested them to make sure they matched our designs and find bugs. I took a break from the project for the following school year, and the programming team did a bit more work that winter. I rejoined the project for summer 2022, staying on through the end of development at the end of summer 2024; at this point, I was the only programmer, and the rest of the old design team was now working on fleshing out how the study would test with students and getting approval for doing so. I produced weekly builds to send to them, and they would test out the new features I had added, followed by all of us discussing whether the new features gave the experience we were expecting them to and deciding what I would work towards for the next week.

# Mechanics
The core mechanics of Gnome Gnolf are putting the ball and completing rigid transformations.

<figure style="display:inline-block;">
    <img
        src="/assets/images/gnome-gnolf-putting.png"
        alt="The same course as shown above, but viewed from the left. Above the course is a smartphone, looking down at the course. Extending out of the right side of the phone is a putter, which is lined up to putt the ball towards the sloped curve."
        />
    <figcaption style="text-align:center;">
        Putting the ball is achieved by swinging a putter that is attached to the phone.
    </figcaption>
</figure>

<figure style="display:inline-block;">
    <img
        src="/assets/images/gnome-gnolf-reflection.png"
        alt="A minigolf-style course with an outer wall in the shape of a duck in profile. In the duck's body, a there is a wing-shaped lake. A ramp points away from the lake, and a ghost version of the ramp is reflected to point across the lake. In between the ramp and its reflection is a gnome, showing the plane across which the ramp is reflected. Next to the gnome is the ball, around which is a yellow cylinder."
        />
    <figcaption style="text-align:center;">
        Players direct gnomes to complete rigid transformations (like reflection) on wooden objects. To perform a transformation, both the gnome and at least part of the object must be within a cylinder around the ball.
    </figcaption>
</figure>

<figure style="display:inline-block;">
    <img
        src="/assets/images/gnome-gnolf-rotation.png"
        alt="A minigolf-style course in which a wooden object is blocking the ball's progress. A gnome stands on top of the object, and a ghost version of the object, having been rotated around the gnome, is in a position such that the player could putt around it. Next to the gnome is the ball, around which is a yellow cylinder. Looking down on the course is a phone aligned with the ghost object, along with a reduced-opacity version of the phone aligned with the object and arrows indicating a rotaion from the reduced-opacity phone to the full-opacity phone."
        />
    <figcaption style="text-align:center;">
        To perform the rigid transformations, players must use embodied interactions, like rotating their phone to specify how much to rotate an object.
    </figcaption>
</figure>

<figure style="display:inline-block;">
    <iframe width="560" height="315" src="https://www.youtube.com/embed/7xWpweBAuOo?si=VIhQaPpydCbtKpSG" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
    <figcaption style="text-align:center;">
        To make the interactions more embodied, players may reposition and scale the course by tapping mushrooms located near the start of the course. This allows players to set the course to match up with some surface in the real world, such as the ground of a park (as shown in the video) or a coffee table.
    </figcaption>
</figure>

