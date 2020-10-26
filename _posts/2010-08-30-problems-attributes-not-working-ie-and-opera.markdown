---
layout: post
title:  "Problems with attributes not working in IE and Opera?"
date:   2010-08-30 00:00:00 +0000
categories: blog
tags: HTML
---
So, what did I do with my bank holiday weekend? I was intrigued by some odd Opera and IE behaviour — that’s what.

I was presented with a site whose styling wasn’t working for certain tags. It was an odd one. I thought it might be an
absolute positioning bug, but testing was bringing up nothing – why on earth would simple CSS styling, nothing special,
fail completely in Opera?

Then I took a closer look at the source — and something caught my eye. There was some malformed HTML:

```
<h1 title="test""style="background-color: #ccc">Test</h1>
```

Gotcha! Removing that innocent looking multiple quote fixed the problem. But I still wasn't happy. Browsers should
recognise and fix badly formed HTML, no? It’s not like a closing tag was completely missing. So I made a basic HTML
template with little more than the h1 tag you see above, and just enough HTML5 to make it validate.

Then I played around with it. What happens if I add a space?

```
<h1 title="test"" style="background-color: #ccc">Test</h1>
```

That fixed it. Hm. Why on earth would the lack of space break things? Lacking a space is completely fine in both HTML
and XHTML. Let’s remove the space again, and test some more. What if I replace the rogue " with another character
– say $?

````
<h1 title="test"$style="background-color: #ccc">Test</h1>
````

Wait — that’s a turnout for the books — it now breaks in Chrome. Then it dawned on me. If I replace that dollar sign
with a normal alphanumeric character — the character ‘a’:

````
<h1 title="test"astyle="background-color: #ccc">Test</h1>
````

That’s it! Without the space between attributes, Opera and Internet Explorer are treating `"style` as the attribute,
with Webkit and Gecko being smart and removing the extra quote. Add the space, and Webkit does the same. Obvious when
you think about it, isn’t it?

So that’s what I did with my bank holiday weekend. What did you do?