---
layout: post
title:      "Where did I leave that semicolon... JS Debugging Techniques"
date:       2020-09-27 13:29:47 -0400
permalink:  where_did_i_leave_that_semicolon_js_debugging_techniques
---

## The console

Most moder web browsers have a built-in debugging functionality known as "the console". How the console functions varies by browser, but being able to access it and utilize it is one of the biggest keys to working in JavaScript. In Chrome, for example, access the console with "ctrl+shift+i". From here you can access a console where you can test code, check on variables, get the assignment of an element on page, and much more!

## Console.log() and YOU

Console.log() is a JavaScript method that outputs a message to the web console. It could be a single string, or any number of Javascript objects. Console.log() gets a bad wrap for being overused, and it definitely can be, but it's great for running a quick test. When writing a function, you can easily get your output by throwing in a console.log(), like this:

`function getList(){
fetch("http://127.0.0.1:3000/data")
.then(resp => resp.json())
.then(data => {console.log(data)}
}`

This will output to your console exactly what data you're fetching, how great is that? Console.log() can be used in a plethora of situations, and is a great tool to quickly test that a function is working or variable assignment is functioning as expected.

## Inspect THIS

Within your browsers console you'll likely find a tool known as the inspector (Chrome shortcut "ctrl+shift+c"). With so much of JavaScript web programming focusing on DOM manipulation, having a tool to easily show you exactly what an element on a page is is a huge advantage. The inspector tool does just that! Use it to select an element on a page, and the inspector will highlight all of it's attributes like class, id, role, etc, and can even show you where it's nested in your HTML! Need to find out how to easily select that element you want to turn into a button? Inspect it!

## Making the Network Work

Also within your console you'll find a tab labeled "Network". There is a log going on in this tab, but one of the most important things for debugging is that the network will show you all requests being sent through your site and their status. For example, as I update this blog, the network tab is telling me that a save function keeps making a successfull patch request whenever I take a break from typing. If you're trying to check to make sure a fetch request is firing and working, look no further than your network tab!

## Debugger

Arguably one of the most powerful tools in the JS toolkit is the debugger statement. Following Mozilla's example of syntax:
`function potentiallyBuggyCode() {
    debugger;
    // do potentially buggy stuff to examine, step through, etc.
}`
The debugger will pause all execution in your script source where it's at. From here, you can jump into your console which will be in scope right where you left your debugger! You can use this to test variable assignments, test out a function, and more, right from your console! If you have a function or a fetch request that isn't working and you're getting stumped, pop a debugger in to break it all down and get a deeper look.

### Of course, there are plenty more debugging tools for JavaScript development, but with a good solid understanding of these basics you're well on your way to becoming an exterminator-level debugger!



