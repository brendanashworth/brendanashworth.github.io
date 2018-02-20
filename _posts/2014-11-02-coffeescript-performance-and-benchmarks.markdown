---
layout: post
title:  "CoffeeScript: Performance and Benchmarks"
date:   2014-11-02 07:42:27 -0700
---
I've been a long-time [CoffeeScript](http://coffeescript.org/) fan; its ability to shorten code, ditch brackets and semicolons, and provide "expressive" ways of writing code was definitely a plus for me. Though I originally learned it some time around 5 o' clock in the morning, the language stayed with me for a purpose: it had become my escape route from JavaScript.

> CoffeeScript is a little language that compiles into JavaScript. Underneath that awkward Java-esque patina, JavaScript has always had a gorgeous heart. CoffeeScript is an attempt to expose the good parts of JavaScript in a simple way.
— *coffeescript.org*

However, as I began writing more and more complex applications in the language, I realized the syntax was just not cutting the deadline. The need for awkward commas, bad object expression and the inconsistent English vs. symbol equality checks were bogging the language down. So I wondered: why was I using CoffeeScript in the first place? [Was it still the answer?](http://www.walkercoderanger.com/blog/2014/03/coffeescript-isnt-the-answer/)

It does add some [cool and useful features](http://openmymind.net/2012/5/16/Ten-Features-I-Like-About-CoffeeScript/), such as forcing the use of strict equality operands (`===` not `==`) and automatically-filling arrays (`[1..50]`), but I figured only one thing would make the difference to me: **speed**.

So, I did what anyone with an inquisitive mind would do: I wrote code and ran benchmarks.

I decided to run tests between three program files against three different tasks commonly done in [Node](http://nodejs.org/). I wrote equivalent files for each task: a `.coffee` file, a compiled from CoffeeScript `.js` file, and an equivalent, custom-written `.js` file -- for control. I wanted to see how these three variations of the same code compared:

* Interpretation via the `coffee` CLI
* Compiled CoffeeScript, run via `node`
* Equivalent JavaScript, also run via `node`

I tested against the following tasks:

* Simple addition loop (add all numbers between 1 and 5000)
* HTTP server (using `node`'s [HTTP module](http://nodejs.org/api/http.html))
* File I/O (simple `node` file streams)

It is safe to say I was **astonished by [the results](https://gist.github.com/brendanashworth/3ad93270f13b3c2eaa5f)**. In the addition loop test, the CoffeeScript command-line interpreter was simply demolished by both other options, and the compiled CoffeeScript was approximately 3% slower than the pure JavaScript alternative -- which was best shown in the [addition loop test](https://gist.github.com/brendanashworth/1de57616718d7514978d).

![CoffeeScript JavaScript Node performance benchmark](/images/2014-11-02/benchmarks.png)

Though the results for compiled CoffeeScript vs. the written JavaScript were as predicted, the `coffee` command line interpreter only does one thing: slow down your program. If you are using the interpreter in production, you've clearly done something wrong.

![dumb cat coffeescript](/images/2014-11-02/cat-in-box.jpg)

In essence, it is best to entirely avoid running the `coffee` interpreter, and only run it when debugging -- if ever. In addition, unless you have a strong reason to stay with CoffeeScript, just go for clean JavaScript -- though the speed increase may not be noticeable, it does not make sense to opt for the speed decrease *and* lose some of the community.
