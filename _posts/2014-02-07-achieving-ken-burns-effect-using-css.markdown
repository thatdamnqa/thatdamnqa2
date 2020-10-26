---
layout: post
title:  "Achieving the Ken Burns effect using CSS"
date:   2014-08-03 00:00:00 +0000
categories: blog
tags: CSS
---
The [Ken Burns effect](http://en.wikipedia.org/wiki/Ken_Burns_Effect) is a common technique used in video-making where
a photograph or image is zoomed in and panned across, to make for more interesting visuals.

This effect can now be achieved using CSS's animations properties. I've made up some example code to give a basic
demonstration of what can be achieved.

To be able to pan across an image, we would need to use a size that's bigger (either taller or wider) than we'll be
showing on the page, and we need to use CSS to tell the browser not to try and squeeze the image to the size we gave it.
We use the object-fit property alongside setting a `width`, `height`, and `overflow` property to do this:

```
img:hover {
    object-fit: cover;
    overflow: hidden;
    width: 300px;
    height: 300px;
}
```

Once we've done that, we need to do the effect! This is achieved using CSS animations. Here, I've used CSS classes
which I give the image to create two different animations depending on whether the image is a landscape or portrait
image: each will pan in a different direction (across or up).

```
.portrait {
    animation: portrait 30s;
}
@keyframes portrait {
    from {
        object-position: bottom;
    } to {
        object-position: top;
    }
}

.landscape{
    animation: landscape 30s;
}
@keyframes landscape {
    from {
        object-position: left;
    } to {
        object-position: right;
    }
}
```

Notice that I've used unprefixed attributes here, but some browsers may need to be prefixed, or may not support either animations or object-fit.