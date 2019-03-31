---
layout: post
title:  "Files not loading in a Virtualbox virtual machine"
date:   2013-08-23 00:00:00 +0000
categories: blog
tags: development
---
Every so often, randomly I see a problem where a virtual machine will only partly load a CSS or Javascript file, and
when you load it in the browser it will have a bunch of strange unicode characters in there

We even [saw it in joind.in](https://joindin.jira.com/browse/JOINDIN-318)

The fix is fairly simple - just edit your vhost configuration and add the following lines:

````
EnableMMAP Off
EnableSendfile Off
````