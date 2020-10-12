---
layout: post
title:      "JavaScript Promises and Asynchronicity"
date:       2020-10-12 21:19:31 +0000
permalink:  javascript_promises_and_asynchronicity
---


To understand the concept of promises in JavaScript, you'd need a little background on how JavaScript functions from the start. JavaScript is what's known as "single-threaded", meaning only one script can run at a time. To bypass this, you can make a function run only when something specific happens, like you would when adding an event listener. Doing this would hold the function script from execution until it's specifically acted upon. This is essentially what makes up the foundation of a Promise in JavaScript!

Promises in JS can be related to promises in real-life! In real life, let's say you promise your roommates that you'll finally clean up your mess in the kitchen. At the end of the day, you've either succeeded in that promise and cleaned your mess, or you didn't, and you failed. In JavaScript, promises function similarly in that the promise either succeeds or fails, and some sort of action is taken based upon that success or failure. Let's build a super basic promise as an example:

```
let promise = new Promise((resolve, reject) => {
let mathed = 1+1
if (mathed == 2){
   resolve("Success")
} else{
   reject("Failure")
	 }
}) 

```

Here our promise is taking in two functions as arguments, resolve() and reject(). We're setting variable mathed equal to 1+1, which equals 2 of course. If mathed is indeed 2, our resolve() function will be executed with argument "success". If mathed doesn't equal 2, our reject() function will run with argument "failure".

This isn't useful quite yet, we'll need to do something with our resolve/reject functions to make them work. This is where ".then" comes into play. Attaching .then to a promise allows you to run a new function upon success of your promise.

```
promise.then((message) => {
   console.log("I've reached the then!" + message)
})

```

In this case, message will be the argument of the success function, "Success". If we change the mathed variable to equal 2+2, our promise would reject, but how do we utilize that rejection? Like .then, we can use .catch to designate what happens when our promise is rejected.

```
promise.catch((message) => {
   console.log("I'm in the catch..." + message)
})
```

So what's the benefit of utilizing a promise? Asynchrony, of course! Asychrony is the act of multiple things happening at the same time. Like I said before, JavaScript is "single-threaded", meaning only one script can run at a time. We can skirt this utilizing promises! In utilizing promises, while other scripts our functioning, we can tell JavaScript to work on this promise function in the background whilst running other scripts, and store the result of our promise for us to use later. This allows us to use promises for time-consuming tasks like pulling a list of all of our users from our database. The promise will pull that list in the background (known as running asynchronously) while our other scripts our running, and store the return of that promise for us to use whenever we like. In web development, the most common usage of this is through the Fetch API.

The Fetch API gives JavaScript an interface for accessing and manipulating data within the HTTP pipeline. In layman's terms, Fetch allows you to utilize Javascript to send/receive or alter data from a website. In its most common usage, Fetch takes in an argument of the path you'd like to fetch resources from, and returns a promise containing the response. Let's build a quick example:

```
fetch('http://fetchexample.com/examples.json')
   .then(response => response.json())
	 .then(data => console.log(data));
```

Our fetch above will grab all examples from the website, and first return a promise containing our response. This isn't actual JSON data, it's just a literal HTTP response object. To extract the data out into something we can use (like JSON!), we'll run the .json() method on that HTTP response object which will extract that content and transform it into JSON. Once we've transformed our response into JSON, we can then take that data and simply log it in the console to check it out. Since .then returns a promise containing the response object, it can run the collection of that data in the background while your other scripts are running, then once it's completed or failed the collection of that data we can chose what to do with it from there.

Utilizing promises is key to web development so you're not bogging down the loading of your page by collecting data. Without promises, you're page would be trying to load with all of your scripts, and when you got to the point of wanting to pull data (let's say pulling a list of users from your backend), you're page load would halt while this data is gathered. By gathering this data into a promise, you can let JavaScript collect the data and hold on to its return for you while other scripts are running, meaning your page can load all of its fun elements WHILE your data is being pulled! How cool!



