---
layout: post
title:  "Writing a good commit message"
date:   2015-07-28 00:00:00 +0000
categories: blog
starred: starred
---
You see, I don't like the term "code review". I prefer "peer review": because you're not just looking at the code.

One thing I like to look at, and which I increasingly find an important part of a commit is the commit message itself.

You may be writing to your future self, to a colleague in another office (or even country), or trying to explain to a project lead why you did what you did. And the commit message is the best way to achieve this.

I can't pretend to be the best writer on the planet: I've done my fair share of "bug fixes" messages, but here's a few things I've picked up:

* Ticket number goes first: it doesn't matter how you do it (although a standard is always good), but if there's a bug tracker ticket number associated with the commit, it should be the first thing you write. It helps automated systems, and makes it easy to pair an issue with a commit.
* One issue per commit: I've been burnt enough times doing this. Nobody enjoys picking out code that isn't ready yet!
* Use the text editor: it may be possible to use a flag such as -m to include an in-line message, but it's worth avoiding using it. Your message will be better for it.
* Include a one-line summary as the first line. Go into more detail after a carriage return. This makes it easy to scan logs, and improves automated systems. Make sure this summary makes sense without the rest of the message!
* Why did you do this? Yes, I can see you've modified the CSS stylesheet. Would you like to tell mewhy?
* Include discussions: future readers may not be privy to a conversation you had with a colleague. Write down what was discussed, with who, if you're doing something out of the ordinary.
* Write a novel if you have to, but keep it succinct. Provide too much information rather than not enough. I'd rather have to skip a paragraph than have to interrupt you in order to ask why you did what you did.
