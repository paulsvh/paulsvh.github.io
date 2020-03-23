---
layout: post
title:      "Do programmers dream of instant debugging?"
date:       2020-03-22 22:31:42 -0400
permalink:  do_programmers_dream_of_instant_debugging
---

Between yesterday and today, I spent about 6 hours working on a single bug, the first time in my relatively-short programming experience in which I've done so. For clarification, it's probably best if I describe my app before I can describe my bug and my fix.

My CLI app takes in a list of all breweries in Los Angeles using HTTParty, and stores each of those breweries and their attributes as individual objects. It then compiles a numbered list of those objects, and allows the user to pick one by number to get extended information (brewery-type, address, phone number, and website). For reference on how it works, check out my flow diagram below.

![](https://i.ibb.co/t4RX7Wc/CLI-Project-Diagram.png)

After about 5 hours I had everything in place and functioning, until I tried to run through my app more than once. The issue I encounterred was as such:
* The app takes in data from my API and used it to create a bunch of brewery objects with their own attributes
* It then prints out a numbered list of said breweries (number. name) and asks the user to pick one
* Once selected, the app divulges the attributes of said brewery
* At this point you can exit the app or continue to look at another brewery, which is where it fell apart

Upon continuing after having already selected a brewery, the CLI printed the list again, but this time it was doubled in length and the objects had repeated. Essentially what was happening was:
* My array, let's call it "brewery_list", looked like this upon initialization
* brewery_list = ["1. Brewery X", "2. Brewery Y", "3. Brewery Z"]
* This worked fine for the first initialization, but after the first run through, when attempting to bring the list up again, you'd get:
* brewery_list = ["1. Brewery X", "2. Brewery Y", "3. Brewery Z", "4. Brewery X", "5. Brewery Y", "6. Brewery Z"]

At the time, I had my CLI class creating and controlling my brewery list. I tried setting the list to its own variable and using brewery_list.clear before it puts'd it out again, I tried refactoring my function that created my brewery list in every way I could think of, I even had a couple cohort-mates look at it, and they didn't get it either. So, after a few hours of head scratching, I set down my keyboard and mouse a defeated man.

I did what I normally do when I don't have to be up early, popping open a beer and finding something on netflix to lazily ignore while I scroll reddit in bed. After watching most of a pretty weird docu-series on big-cat exotic park owners, I turned off my light and laid down to sleep. My mind drifted, but for whatever reason I was running through my app in my head and a lightbulb went off. "Why is my CLI class creating and controlling my list of brewery objects? Why isn't my brewery class doing that and then my CLI class can just call that method when I need it?"  Great question tired Paul, great question. I turned on my light, grabbed my nearby notepad, and jotted down some notes:
* Move method for creating brewery list to brewery class
* Store brewery list in class variable
* Use class variable in CLI class to puts out the list

The next morning, I got to work implementing said changes. It took me a little bit to figure it out, but I eventually managed to make a brewery class function that emptied a class variable for my list array, and re-made it should that function need to be called repeatedly, which I found out can happen in certain use cases. Here's what I ended up with for the list:
```
def self.wipe
   	@@list.clear
   	@@all.clear
   end

   def self.make_list
   	wipe
   	API.get_breweries
    self.all.shift
    @@list << self.all.map.with_index(1) do |brewery, index|     
     "#{index}. #{brewery.name}"
 	end
   end
```
@@all is a class variable holding all brewery instances in an array. @@list is an array that's populated with strings of "number, name". Utilizing my class method "wipe" I was able to reset both @@all and @@list before re-making the numbered list, should it need to be re-made.

That's it, it took me far longer than I would have thought, and at the end of the day it seemed like such a simple bug, but there's a big lesson that I'm learning here. A lot of our future careers will involve a ton of that head-scratching, playing around, figure-out-what's-broken time. It can be annoying, it can be frustrating, but at the end of the day, getting to that solution is such an incredible feeling that it makes it all worth it!
