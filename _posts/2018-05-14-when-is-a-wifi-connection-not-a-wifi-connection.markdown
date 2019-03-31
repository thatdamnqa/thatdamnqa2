---
layout: post
title:  "When is a wifi connection not a wifi connection?"
date:   2018-05-14 00:00:00 +0000
categories: blog
---

So, when building apps we always check that the app fails correctly with the correct error message when the phone is offline. But what if the phone reports as being online, but the data isn't what you expect it to be?

This is a common state, and a very common case of this happening is when the user receives a [captive portal](https://en.wikipedia.org/wiki/Captive_portal), usually when first connecting to a public wifi. We need to ensure that the app doesn't behave in unexpected ways in this case.

There's a way you can check this, without needing to visit your local cafe. It can be checked with [Charles Proxy](https://www.charlesproxy.com/). (If you don't have this tool, then you should go and get it. It's pretty awesome)

Once you've got Charles Proxy up and running, and your device talking to the proxy (there's instructions elsewhere on [how to connect your phone to Charles Proxy](https://www.charlesproxy.com/documentation/faqs/using-charles-from-an-iphone/)), you can use the Map Local tool test this scenario.

* First, you'll need to create your "portal" to return. This can be something as simple as a text file, or as complex as a full webpage. The tool will return any file you give it.
* Then, in Charles Proxy, go to `Tools -> Map Local`
* Ensure that `Enable Map Local` is switched on
* Click `Add` to create a new rule
* You don't need to fill in all these fields: I've got this feature working by completing the "Protocol" and "Host" fields inside the `Map From` section, and "Local path" from `Map To`.
  * Inside `Protocol` and `Host` I enter the domain of the URL I want to overwrite (eg. "http" and "thatdamnqa.com")
  * Inside `Local path` I enter the path of the file I want to send instead

*This blog post was written as part of [Ministry of Testing's Blogger's Club](https://club.ministryoftesting.com/t/sprint-1-a-technical-tip-all-testers-should-know/14619).*