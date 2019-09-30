---
layout: post
title:  "Checkbox Testing"
date:   2019-09-30 00:00:00 +0000
categories: blog
---

*Checkbox testing (n.): the act of running a pre-defined set of tests to confirm that the software is working.*

But there’s so much wrong with the act of checkbox testing. As part of a wider testing strategy, it does have its
place. But it’s often seen a lot as being the only method of testing a new feature, and this is where the problem lies.
Let me explain why.

### “A pre-defined set of tests”
Having some kind of plan of how to start testing a feature or a product is never a bad thing, especially if there’s a
lot of testing to be done and there are things that you really must check.

The problem lies when you forget to go off this happy path, and wander around the app. Because the times you ask
yourself “I wonder what happens if…?” are the times you often find those hidden bugs.

Going through the same list isn’t necessarily a bad thing: it reminds you of the important parts of the software that
needs to be checked in your regression testing. However, you need to let yourself try things out. If you see a button
you haven’t pressed in a while, or you hear about something else a colleague found the other week, you should let
yourself go off on a tangent and see what happens.

### “Confirm that the software is working”
This might sound like arguing semantics, but I really think that there’s a difference between saying that a tester
“confirms the software is working” and that a tester “looks for any problems in the software”.

The latter gives the tester the mindset that there has to be problems in the software; that it only needs to be
found. On the other hand, by saying that the tester confirms software is working, you’re already suggesting that the
software is bug free, and you’re just looking to prove it. Because of human bias, we’re more likely to miss a bug if
we don’t _really_ want to find any.

### Beware of automated checkbox testing
Originally, I thought that checkbox testing was a trap you can fall in when doing manual testing. But I’ve seen
realised that you can do automated checkbox testing, too.

Just as with manual testing, you need to avoid the trap of “confirming that it works”. If your automation is quick
enough, your automation can be used to not only check those edge cases that you would in regular exploratory testing,
but you can also use automation to check for the edge cases that you _can’t_ easily check with regular exploratory
testing. With scripting, you can do things that would normally be tricky or time consuming to do manually. Be it
check a large set of test data, or change the environment under test such as configuration, network connectivity,
and even timezone.
