---
layout: link
title:  "Maybe we could tone down the JavaScript"
date:   2016-03-08 00:00:00 +0000
categories: blog
link: https://eev.ee/blog/2016/03/06/maybe-we-could-tone-down-the-javascript/
tags: Javascript Quality
---

Something that's been on my mind for some time, but have never been able to find a way to put it across. Eevee does it perfectly:

>Accept that sometimes, or for some people, your JavaScript will not work. Put some thought into what that means. Err on the side of basing your work on existing HTML mechanisms whenever you can.

Yes! We have (largely) moved on from noscript tags, but javascript can (and does) do weird things in weird ways, simply because you can't control the environment.

So whenever you can, don't expect your scripts to download, or work.

Or, as I like to think about it: if you are rewriting a browser control, ask yourself why.
