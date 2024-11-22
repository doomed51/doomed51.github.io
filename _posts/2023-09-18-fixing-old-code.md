---
layout: post_custom
title: Fixing Old Code
tags: [business]
author: Rachit 
---

I’ve been fixing old code recently. Some of the stuff I wrote very early on relative to the lifespan of my current project. The code in question is central to the functionality of the entire system therefore gets used frequently in logic across different parts of the system.

This is some of the most hastily written, discombobulated shit I’ve had to deal with. I know why its like it too, because all I was thinking at the time was ‘just make it work and get something useful out of it’. So I moved on from it the moment I was able to get some kind of front-end user value. I kept deferring taking better care of it. 

This frames technical debt in a different perspective for me. It says to me that special attention needs to be given to parts of the system that get *used* frequently as opposed to those that get *changed* frequently. Priority should be set according to frequency of use agnostic of whether it is a person or another system using the system. 

Things that get changed frequently usually relate to a front-end user need. Whereas there are parts of the system that get utilized by the *system* frequently and not necessarily the user.  Even though I have followed the principle of ‘every time a module gets touched, it should get easier to change the next time’, it has left a very painful gap.

### Today’s post was brought to you by *'Discombobulation'* 

#### Discombobulation  

**Noun** (informal, mainly humorous)  

The fact of being made to feel confused or uncomfortable by something:  

- *He showed his discombobulation by not being sure whether to sarcastically congratulate his rival or attack him.*  
- *We feel nostalgia for the past and discombobulation about the future.*  
- *The code left him discombobulated* 