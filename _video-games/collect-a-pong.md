---
title: "Collect-A-Pong"
date: 2022-03-17
---
[You can play the live build here!](https://nemeanlion42.github.io/Collect-A-Pong/){:target="_blank"}\
[You can view the source here!](https://github.com/NemeanLion42/Collect-A-Pong){:target="_blank"}

![Demo](/assets/images/collect-a-pong-screenshot.png)

# Overview
This is a game I worked on as part of **CMS.611J/6.073 Creating Video Games** at MIT. This assignment entailed prototyping a game that focused on one primary mechanic and a small number of secondary mechanics.

# Mechanics
As the inspiration behind this game was to make a spin on Pong, my team chose the primary mechanic "XY Movement on a plane" and considered several secondary mechanics over the course of prototyping:

- Bouncing
- Picking up collectables
- A scoring system
- Interaction with obstacles
- Visual puzzles
- Power-ups

In selecting from our brainstormed mechanics, we considered the following factors:

- What keeps us within a reasonable scope for about a month of development?
- What makes the game easy to start but challenging to master?
- What creates a satisfying build-up and release of tension?

Ultimately, we decided to move forward with bouncing, picking up collectables, and a scoring system.

# Final Game Summary
Upon loading the game, the player is presented with the choice of Easy, Medium, or Hard. Once they choose a difficulty, they enter the main game. The player has control of four Pong-like paddles (styled as candles), one on each edge, that track the mouse around the screen. Starting in the center of the screen is a ball (styled as a ghost) that starts moving in a random direction at an initial speed determined by the difficulty selected. If the ball hits a paddle, it will bounce off, moving in a direction radially away from the center of the paddle. There is also a coin at a random position in the play area; if the ball hits the coin, the player gains a large chunk of points and a new coin spawns. As play continues, the player slowly gains points just for keeping the ball in the play area, and the ball speeds up at a rate determined by the difficulty selected. Eventually, the player fails to hit the ball, it hits the edge of the screen, and the game ends and immediately restarts, allowing the player to try again.

<video src="/assets/videos/collect-a-pong.mkv" width="640" height="360" controls></video>

# Prototyping
For this assignment, we were presented with the option to create multiple standalone prototypes or to continue building on a single one. We were then asked to evaluate the pros and cons of the approach we chose. My team chose to continue building on a single prototype throughout the length of development, and we observed the following pros and cons:

| Pros | Cons |
| ---- | ---- |
| Easy to track changes over time | Committed to a basic structure early on |
| We could start improving and focusing on one idea quickly | We don't spend time exploring vastly different options |
| We don't waste time or energy on separate prototypes while already having a general idea of what we want | |

# Questions To Answer
We had several questions that we wanted to answer through our prototype, which we answered through a combination of just thinking about our design and conducting several playtests.

## How can we allow control of four paddles without requiring too much user input?
We considered several options for how to implement control of the paddles, finally settling on having the paddles at the top and bottom of the screen take the mouse's x-position and the paddles at the left and right of the screen take its y-position.

One of the major considerations in designing this input scheme was whether we wanted to allow the player to control all four paddles independently or just each pair of opposite paddles. Allowing full control of all four paddles could allow advanced players to set up an interesting series of bounces ahead of time, but for most players it would just be more mental load for little to no benefit, so we went with just controlling each pair of opposite paddles.

Once we had landed on controlling pairs of opposite paddles, which essentially amounts to picking an xy-position to align the paddles to, we had to decide how to control that point. As we were developing this game to be deployed to a browser, we only really considered mouse and keyboard as input options. Keyboard would allow us to fully isolate each axis of paddle movement and would have the benefit of being universally available (even on laptops), but we then have the problem of what keys to use. WASD is a pretty accepted standard for many games, but not everyone would necessarily be familiar with it (which we could accomodate with more on-screen instructions), and different keyboard layouts may make WASD inconvenient or even unusable (even if we use physical keycodes, some custom keyboards allow you to change the physical keycodes being sent, not just the interpreted keypresses). The arrow keys are even more universal, even if they aren't many gamers' first instinct, but they may also be inconvenient on some keyboards, such as those with a [60% layout](https://www.keyboard.university/100-courses/keyboard-sizes-layouts-gdeby){:target="_blank"} (which I personally use). We could have added an options menu that allowed the user to set the keys used to control the paddles, but that could bog down what is supposed to be a quick experience to jump into. Using the mouse allows the player to clearly see the position that the paddles are tracking (since it's just where their cursor is), and it will generally be immediately apparent to players that the mouse moves the paddles since they can only start the game by clicking through the menu, and most people will move the mouse at least a little bit after clicking the button, even if it was just to take their hand off of the mouse. The mouse is, however, even less standardized than keyboards; mice, touchpads, trackpoints, and trackballs all behave differently, and some are more suited to the quick, precise movements that real-time games (including this one) tend to demand. In then end, we decided to go with the mouse, partly just because of the ease of implementation.

## How can we make the ball/paddle behavior familiar, but still new and surprising?
We felt it was important to keep the Pong aiming system, in which the ball bounces at an angle proportional to how far from the center of the paddle it hits.

By putting a paddle on each edge of the screen and having the player control all four of them, we'd already deviated decently far from Pong, but we also made it so that rather than ever bounce off the edges of the screen, the ball is lost if it hits any edge.

## How do we ensure a balanced level of control for the player?
There are two things the player wants to control to succeed in this game: whether the ball is hit and at what angle it then moves. We want the player to have enough control that, with enough skill, they can fully control both of these (though maybe not directly), but not quite so much control that it feels impossible to fail.

This problem had basically been solved for us by [Allan Alcorn](https://en.wikipedia.org/wiki/Allan_Alcorn){:target="_blank"} (the creator of Pong). Having the ball bounce at an angle proportional to how far from the center of the paddle it hits gives the player two levels of success for each hit. First, did they hit the ball at all? If they did, great! They don't lose! If not, they get to start over. If they did hit it, though, where did it bounce to, and for this game, does that trajectory send it into the coin? This second level of success even has something of a partial success, where they may not get the coin on this bounce, but they may set up their next hit to more easily get it.

## How do we enocurage multiple rounds played in rapid succession?
This one was pretty simple --- add a score counter. With a score, the player has a way to measure their progress and something to try to beat. Even better, keep track of their high score so they don't have to.

## What can we add that allows players to show off their mastery?
Again, just add a score counter and high score tracker. This immediately lets players compete to see who can get the highest score. In addition, having the score be made up of not just the time without missing the ball but also the number of coins collected allows confident players to try to get points faster.

# Playtesting
As we worked on our prototype, we conducted several playtests, which taught us several things about the state of our prototype and led to several design changes.

| What We Learned | What We Changed |
| --------------- | --------------- |
| Players were often surprised by the direction the ball bounced | Added radial lines to paddles to clue players about the radial bouncing |
| The rate of ball acceleration was easy to deal with at the beginning and then grew challenging over time, which was good for new players, but experienced players wanted a faster initial ball speed | Added Easy, Medium, and Hard modes (harder modes have faster initial ball speed and acceleration) |
| Players don't want to track multiple goals even if they have multiple goals | Combined time in arena and coin collection into a single score (they were previously shown as simply a time and a number of coins) |
| Player goal shifts from "collect coins" to "survive" as ball speed increases | Added high score tracking |
| Many players thought collecting coins increased the ball speed (this was never true) | |
