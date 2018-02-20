---
layout: post
title:  "Introduction to Advanced JavaScript Prototyping"
date:   2014-10-19 06:25:20 -0700
---
JavaScript has its own unique implementation of object oriented programming: the prototype system.

This article will explore deep into this concept: how it works, how to use it correctly, and how to take advantage of JavaScript's various features to do new things you've never done before.

First off, JavaScript prototyping is based off of two concepts:

### The `.prototype` variable
In JavaScript, each `Function` has its own `.prototype` key, of type `Object {}`. You can assign specific methods to this variable, which will be used by the object.

### The `new` keyword
The `new` keyword instantiates an object via a constructor that is the next supplied set of characters (i.e., `var obj = new Cat()`). First, this creates a new `Object {}`, which is referenced within the `.prototype` declarations and constructor as `this`. Then, it copies the constructor's `.prototype` values to the new `Object.__proto__`; finally, it returns the newly created `Object`.

The following are the gears behind the beauty. If you have a variable and reference part of it (i.e. `object.undefVar`) that has a value of undefined, it will also check the `__proto__` part of it to see whether it has a key of that value (`object.__proto__.undefVar`). In example,

<script src="https://gist.github.com/brendanashworth/6696b6a45a3b78e474ad.js"></script>

This will print out "Success" to the screen. Isn't that cool? This is the magic behind JavaScript prototyping. Now, lets get to work with a few working examples of object oriented JavaScript.

For our example, we'll have a set of Clients we want to have.

<script src="https://gist.github.com/brendanashworth/67d3f0325e47f5009396.js"></script>

After defining both functions, it will then create a new `Client` and `.contact()` that client. **Note:** if you've  been paying attention thus far, `.contact()` is actually just an alias for `.__proto__.contact()`.

Now, this special `__proto__` object can have key/value pairs containing more than just `Function`s. It actually works with any JavaScript variable. For example, this is valid JavaScript:

<script src="https://gist.github.com/brendanashworth/c5c5041ef9f84d8e95af.js"></script>

Prototypes have a lower priority than other values in the same `Object`. You can take advantage of this for default values, such as this:

<script src="https://gist.github.com/brendanashworth/32b1f0f81fe5e6b42977.js"></script>

With this, you can create a new `Person` with age of 16 while their age will be stored as 18; on the contrary, if you created one with age 24, their age would be stored as 24. Prototypes are only referenced and used when the `Object` does not have a value for that key itself.

Prototypes are incredibly useful and one of the more powerful tools within the JavaScript language. They are a necessity to learn - and their usage is incredibly widespread.
