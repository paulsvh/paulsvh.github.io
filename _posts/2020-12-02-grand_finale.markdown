---
layout: post
title:      "Get Hooked: Simplicity In State Through React Hooks"
date:       2020-12-02 21:10:00 -0500
permalink:  grand_finale
---

Hooks are a new feature added to React as of version 16.8, and if you're using React at all you probably already know how useful they've become. Whereas before, if you wanted to use state and certain other features, you needed to do so within a class-based component. With the introduction of hooks, users can now get access to state in a functional component through the useState hook. Let's dive a little deeper into how it works and how to use it.

Getting started using state on a functional component is simple, and like most things in React, starts with importing the function into your project. You can import useState in the same line as your React import, so simple!

```
import React, { useState } from 'react';
```

The useState hook returns two variables and takes in a single argument. The first variable returned by useState represents the value of the state, similar to what this.state would represent in a class-based component. The second variable returned by useState is a function used to update the state, similar to this.setState within a class. Typically these are built with a bit of destructuring for aesthetic purposes, which I'll demonstrate in the example below where we'll set up a basic counter function. The one argument useState takes in is used to set the initial state value, which in the example below is set to 0.

```
const [counter, setCounter] = useState(0);
```

For those unfamiliar or having trouble with array destructuring, as I know I certainly was when first introduced to it, the above can be broken down very simply. Within our brackets we're defining two new variables, which we can define however we like. These two variables will be set to the first 2 values returned by useState. To break it down further:

```
var counterStateVariable = useState(0);
var counter = counterStateVariable[0];
var setCounter = counterStateVariable[1];
```

When a state variable is declared with useState, it returns an array with two items, the first being the current state value, and the second being the function that lets us update the state. Creating and accessing them in the direct example above is a bit wonky, which is why we prefer array destructuring, it just takes some getting used to!

Seeing as how we're keeping an integer in the state in the example above, it should be noted that an added benefit of useState is the ability to store numbers or strings in our state, whereas in a class component state has to be defined within an object. In a class component, the state in the example above would look something like this: 

```
this.state = { counter: 0 };
```

So we've now declared our state and set it to a variable (counter), how do we access it? In a class component it would have been something like:
```
<p>This counter has been clicked {this.state.counter} times</p>
```
But with the useState hook and a functional component, it's even simpler, as you can call on the counter variable directly.
```
<p>This counter has been clicked {counter} times</p>
```

So we've set our state and a function to update it, and we know how to call it for usage, let's move on to updating our state. As mentioned before, if we were in a class we'd be using this.setState in something that looks like:
```
<button onClick={() => this.setState({ counter: this.state.count + 1 })}>
```
Thanks to the useState hook in our functional component we already have "counter" tied to our state value and "setCounter" tied to the function needed to update our state, so the update looks much simpler:
```
<button onClick={() => setCounter( counter + 1 )}>
```
Clicking the button will, using our setCounter function that we've made available to update our state, set our state to whatever the current value of counter is, plus 1. This is the buildout for a basic counter button function in React using the useState hook. 

Hopefully this short breakdown gives you an idea of the simplicity and ease supplied with the useState hook, and the benefits of it versus the traditional class-based method way. While there are obviously situations where a class-based component makes the most sense, this new hook gives us the ability to add state to simple functional components, speeding up the creation of simple and clean components. While useState is certainly very important, it's not the only hook that was introduced in React 16.8, there are more (like the extremely useful useEffect and useContext), and React even allows you to build your own hooks to extract component logic into reusable functions!

You can check out more information on React hooks at the official React documentation [here](https://reactjs.org/docs/hooks-intro.html), happy front-ending!


