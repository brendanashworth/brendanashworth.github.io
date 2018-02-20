---
layout: post
title:  "How to use the Node.js EventEmitter"
date:   2014-10-18 18:23:08 -0700
---
The [Node.js EventEmitter](http://nodejs.org/api/events.html) may very well be the single most useful library in the entire Node.js stack. Used all throughout various modules on the internet and even used *basically everywhere* in the Node.js source, the Event Emitter is an extremely powerful tool that is simply waiting to be used by you.

For this tutorial, we'll be using the simple analogy of a cat that meows.

Node.js is asynchronous and intended to be fast -- this is why the Event Emitter was developed. Once Node.js became evented, all of a sudden software developers could take advantage of speeds never before possible inside a virtual machine; this is because you don't need to wait for blocking functions to return -- primarily I/O.

However, we can't wait for our cats to meow! We need to execute some logic within our main execution thread while not waiting for the cat to do something. This is when we need the Node.js Event Emitter.

<script src="https://gist.github.com/brendanashworth/c02e51d4c756c4355480.js"></script>

I'll be walking through all this code to explain to you how the EventEmitter works and how to implement it within your Node.js application.

First, we have the imports -- in this example we're using both the [`util`](http://nodejs.org/api/util.html) and the [`events`](http://nodejs.org/api/events.html) modules, both of which are built-ins to Node.js. We're using the `util` module to apply the Event Emitter `prototype`s to our `Cat` object; please note that we use `util.inherits()` *before* we add our own prototypal methods. This is because `util.inherits()` overrides any previous prototypal methods we declared.

The `events` module holds the EventEmitter -- located at `events.EventEmitter`. You can construct an EventEmitter yourself by using `new events.EventEmitter()`, but it is typically recommended to inherit the properties to your own object beforehand.

Next in the code, we have the object prototype definitions and constructor. Since it is beyond the scope of the tutorial, I won't go into the prototype system -- however, [this article](http://blog.ashworth.in/2014/10/19/introduction-to-advanced-javascript-prototyping) explains the prototype system very well, if you'd like some background on that.

Then, we have the actual EventEmitter code.

<script src="https://gist.github.com/brendanashworth/ebce0ce62b842fd08e4d.js"></script>

The EventEmitter has two basic operations we'll be using: `on` and `emit`. The EventEmitter itself is only a messenger between when you emit / call an event and when you listen to an event.

In our example, we want to print out to the console (via `console.log`) when our `Cat` meows with a message (obviously, our cat can talk -- welcome to Node.js). The way to do this is to add an event listener -- via `on`.

Since the event we're listening for is named `meow`, we simply use

<script src="https://gist.github.com/brendanashworth/0aea19fed250df228c65.js"></script>

> [Documentation for `.on`](http://nodejs.org/api/events.html#events_emitter_on_event_listener)

Note that the `meow` event comes with an argument -- this is supported by the Event Emitter. Any time a `meow` event is emitted, our function will be called with the given argument.

Now we need to call the `meow` event; this is even simpler.

<script src="https://gist.github.com/brendanashworth/153ce4b5efcdc5be51ff.js"></script>

> [Documentation for `.emit`](http://nodejs.org/api/events.html#events_emitter_emit_event_arg1_arg2)

The arguments after `.emit` are optional, and it is up to you whether you'd like to attach arguments to your events.

That is it for the tutorial!  You now have basic knowledge of the [Node.js Event Emitter](http://nodejs.org/api/events.html#events_class_events_eventemitter).

> You can also [use the same Event Emitter](https://github.com/scottcorgan/tiny-emitter#install) in the browser via [Browserify](http://browserify.org/).
