---
layout: post
title: "Fixing old code"
tags: ['systems, business']
author: 
    Rachit 
---

I’ve been fixing old code recently. Some of the stuff I wrote very early in the relative lifespan of my current project. The code in question is central functionality in the system, and therefore frequently interacts with other parts of the sytem.

As I dove into it I realized that this was some of the most hastily written, discombobulated shit I’ve had to deal with in a long time. And theres a good reason for it. The thought was to ‘just make it work and get something useful out of it’. So I moved on from it the moment it got me the outputs needed. I wanted to validate an idea before spending time making the backend do things nicely. 

Well ideas were validated but the backend was kept in the dark. After that, I simply deferred taking care of it and my entire system slowly deteriorated over time as I bent and twisted so I could avoid directly dealing with jank code.  

After that, I kept putting it off, and over time my whole system slowly degraded as I twisted and patched things to avoid confronting the messy code.

This frames technical debt in a different perspective for me. It says to me that special attention needs to be given to parts of the system that get *used* frequently as opposed to those that get *changed* frequently. Priority should be set according to frequency of use agnostic of whether it is a person or another system using the system. 

Things that get changed frequently usually relate to a front-end user need. Whereas there are parts of the system that get utilized by the *system* frequently and not necessarily the user.  Even though I have followed the principle of ‘every time a module gets touched, it should get easier to change the next time’, it has left a very painful gap.

*Today’s post was brought to you by discombobulation* 

discombobulation https://dictionary.cambridge.org/dictionary/english/discombobulation

noun [[ U ]](https://dictionary.cambridge.org/help/codes.html)

informal mainly humorous

the [fact](https://dictionary.cambridge.org/dictionary/english/fact) of being made to [feel](https://dictionary.cambridge.org/dictionary/english/feel) [confused](https://dictionary.cambridge.org/dictionary/english/confused) or [uncomfortable](https://dictionary.cambridge.org/dictionary/english/uncomfortable) by something:

He [showed](https://dictionary.cambridge.org/dictionary/english/show) his discombobulation by not being [sure](https://dictionary.cambridge.org/dictionary/english/sure) whether to [sarcastically](https://dictionary.cambridge.org/dictionary/english/sarcastically) [congratulate](https://dictionary.cambridge.org/dictionary/english/congratulate) his [rival](https://dictionary.cambridge.org/dictionary/english/rival) or [attack](https://dictionary.cambridge.org/dictionary/english/attack) him.

We [feel](https://dictionary.cambridge.org/dictionary/english/feel) [nostalgia](https://dictionary.cambridge.org/dictionary/english/nostalgia) for the past and discombobulation about the [future](https://dictionary.cambridge.org/dictionary/english/future).