---
layout: post
title:  "Switching branches in Subversion without losing changes"
date:   2013-07-26 00:00:00 +0000
categories: blog
tags: SVN
---
The problem: you want to switch branches in Subversion, but you've got changes in your local code that you're not ready
to commit

The solution: export a patch that you can store somewhere safe (or even commit into the repo so others can see it or
work on it)

To export all changes, use svn diff to create a patch file:

````
svn diff > fix-that-annoying-bug.diff
````

As a sidenote, if I'm using a bug tracker, I like to put the bug ID in the filename: not only does this keep all the
different projects together, it makes it easy to know what exactly the code changes does:

````
svn diff > myproject-1234-fix-that-annoying-bug.diff
````

From there I can revert all changes and switch branch:

````
svn revert -R . svn switch http://svn.example.com/my-new-branch/
````

Once I'm done with the new branch and want to go back, and assuming I've committed all my changes I switch back to my
old branch:

````
svn switch http://svn.example.com/my-original-branch/
````

And I import my original changes patch file to start work again, carrying on from where I left off:

````
patch -p0 -i fix-that-annoying-bug.diff
````