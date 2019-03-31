---
layout: post
title:  "Setting the proxy for command-line OS X"
date:   2013-09-22 00:00:00 +0000
categories: blog
tags: development
---
In OS X, it's pretty simple to set a Location to set a proxy for whenever you're somewhere you need to use one

However, this doesn't affect some commandline applications, such as Homebrew. If you want to send this through a proxy,
you'll have to edit `.curlrc` to read something like

```
proxy = proxy.example.com:8080
```