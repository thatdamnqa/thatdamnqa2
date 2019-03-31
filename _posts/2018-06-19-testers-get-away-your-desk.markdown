---
layout: post
title:  "Testers, get away from your desk"
date:   2018-06-19 00:00:00 +0000
categories: blog
starred: starred
---

I'm writing this blog post as part of the [Ministry of Testing Blogger's Club](https://club.ministryoftesting.com/t/sprint-4-what-s-the-non-technical-skill-that-every-tester-should-have-but-most-don-t-seem-to/15759). The subject is *"What’s the non-technical skill that every tester should have, but most don’t seem to?"*. Most answers in the thread seem to involve communication, in some form. As important as communication is, most testers have reasonable skills in this.

I think there's something else we're missing. It's an easy skill to pick up, it's the least technical one you can think of. We've being doing it all our lives, yet we forget to do it while testing.

It's to get away from your desk while testing.

Most of the time, while we're testing, we're usually testing on a high speed network connection, on a good quality computer or device, in a room with minimal screen glare and good lighting, in an office environment. But our users don't always use our products in that way.

In my time as a tester, I've tested several different products. I've tested web games, mobile games, casino games, corporate apps, and internal tools. Few of these will be used in an office setting, so why am I testing these in an office setting?

Of course, I'm not perfect with this. I should definitely follow my advice a lot more. But getting away from the desk can help with a lot of test cases, including but not limited to:

* Network connectivity is poor
* Network connectivity is non-existent
* Network connectivity is non-existent, but the phone reports that there is one
* User is in motion (on a train, or a bus), which could cause network problems
* User is in motion, which could make it harder for the user to read or use the touchscreen
* User can't use sound because it will disturb others (and theres no headphones), or there's background noise
* Screen glare from the sun
* Screen is being used in a dull/dark environment
* User is distracted by environment
* User is in a confined space (eg. on a bus) so has minimal use of gestures
* User is using an old computer
* User isn't using a top of the range desk/chair
* User is using a laptop/tablet on a sofa/in bed
* User is using a mobile phone lying on their side in bed

So, next time you're doing some testing, have a think: is this how the user is going to be using the product? Are there other ways people will be interacting with it? Is there somewhere else I can go or something I can do?

(As an example, I once found a few bugs on an iPhone app by taking public transport into town and using the app on route. It turns out, HTTP requests were failing with the poor network connectivity on the route, which caused some interesting behaviour)
