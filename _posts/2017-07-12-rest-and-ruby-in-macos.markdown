---
layout: post
title:  "Rest and Ruby in MacOS"
date:   2017-07-12 00:00:00 +0000
categories: blog
tags: Ruby macOS
---

If you're getting the following error in Ruby, and no matter what you do you just can't fix it:

    /System/Library/Frameworks/Ruby.framework/Versions/2.0/usr/lib/ruby/2.0.0/net/http.rb:921:in `connect': Connection reset by peer - SSL_connect (Errno::ECONNRESET)

Try using a non-system version of Ruby. I used brew to install it, but it doesn't seem to matter how you accomplish it.
