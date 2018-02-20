---
layout: post
title:  "The Advent of Clib: the C Package Manager"
date:   2014-10-19 06:39:47 -0700
---
#### The problem

If you're a C programmer, you probably know this happens *too much*: various `.c` and `.h` files thrown about a repository -- all of them in the single `src` folder and many of them from many different authors. There can be popular dependencies such as [OpenSSL](https://www.openssl.org/) and [Joyent's HTTP parser](https://github.com/joyent/http-parser) -- all of them under different licenses, carrying different code standards, and rarely being correctly handled when there are updates -- even critical security updates.

> Despite the ubiquitous nature of C it’s sometimes difficult to find just what you need, and you’re especially lucky if it’s not part of some gigantic library of unrelated code.
— *TJ Holowaychuk*

This [issue](http://programmers.stackexchange.com/questions/170679/why-are-there-no-package-management-systems-for-c-and-c) needed to be fixed. After 40 years of being a language, C was still running into the same issues. This needed to end. Then, one day, it did.

#### The solution

[Clib](https://github.com/clibs/clib) is a C package manager for the modern world - one that helps prevent programmers from reinventing a wheel that has already been invented tenfold. It already has [many various packages](https://github.com/clibs/clib/wiki/Packages)  that span from executables to benchmarking utilities, from simple string modification to even Golang `chans` in C. Finally: a place where C programmers can get together and collaborate on open source, then distribute their code - in a centralized, easy way.

#### History

Clib was founded by TJ Holowaychuk (creator of Express.js). He created the original Node.js app, until Stephen Mathieson became the maintainer and ported the entire application to C. It is still primarily maintained by Stephen Mathieson, but he now has a group of contributors joining in on the project.

#### Getting started

Publishing a package is quite easy -- all you have to do is make a `package.json` file with the right keys, and edit it straight to the wiki.

This is an example `package.json` from my [C benchmarking library](https://github.com/brendanashworth/bench):

<script src="https://gist.github.com/brendanashworth/5b46a4e38c909c139037.js"></script>

As you can see, simplicity is key. Just commit it to GitHub and edit it into the [package list](https://github.com/clibs/clib/wiki/Packages); then install it with a simple `clib install <username>/<repo>`.

For years, C programmers have wanted a single package manager to handle the dependencies used in their massive projects; the future is now. [Clib](https://github.com/clibs/clib) is here. [What are you waiting for?](https://github.com/clibs/clib#installation)
