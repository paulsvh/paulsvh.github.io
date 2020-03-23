---
layout: post
title:      "Do programmers dream of instant debugging?"
date:       2020-03-23 02:31:41 +0000
permalink:  do_programmers_dream_of_instant_debugging
---

Between yesterday and today, I spent about 6 hours working on a single bug, the first time in my relatively-short programming experience in which I've done so. For clarification, it's probably best if I describe my app before I can describe my bug and my fix.

My CLI app takes in a list of all breweries in Los Angeles using HTTParty, and stores each of those breweries and their attributes as individual objects. It then compiles a numbered list of those objects, and allows the user to pick one by number to get extended information (brewery-type, address, phone number, and website). For reference, see below.

![](https://drive.google.com/open?id=1nEKBISziH-7PaukaE9OXFWudbnTHlNY8)
