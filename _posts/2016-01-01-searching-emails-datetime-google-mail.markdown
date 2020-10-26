---
layout: post
title:  "Searching for emails by date/time in Google Mail"
date:   2016-01-01 00:00:00 +0000
categories: blog
tags: Gmail
---

I've recently had need to search for emails received after a specific time: as in, "After 3pm on the 1st January 2016", and not "After the 1st January 2016".

[Google's documentation](https://support.google.com/mail/answer/7190?hl=en) isn't very helpful with this, and all I could find on Google's help pages are [unhelpful "nope" answers](https://productforums.google.com/forum/#!topic/gmail/ANLd2eTCNLM).

I disbelieved that this is something Google would neglect to allow for so long. Luckily, I was correct.

You can achieve this if you use the [Epoch timestamp](http://www.epochconverter.com/) instead. For example, to get all emails sent/received since 3pm on the 1st January 2016 (in GMT), all I need to do is search for:

    after:1451660400
