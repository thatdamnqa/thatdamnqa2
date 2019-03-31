---
layout: post
title:  "Reusing primary keys in MySQL"
date:   2010-01-22 00:00:00 +0000
categories: blog
tags: development
---
I’ve recently had need to reuse the primary key for a table whenever a row gets deleted, for example if a row of ID 5 gets deleted, the next entry will re-use the ID of 5. Usually this causes problems with foreign keys, but as no other table had a foreign key linked to this table, it would cause no problems.

The biggest hurdle was finding what the first missing primary key actually is. This takes a bit of SQL, but the following almost gets it:

````
SELECT MIN(table.id + 1) AS nextID FROM table LEFT JOIN table t1 ON table.id + 1 = t1.id WHERE t1.id IS NULL
````

I say almost, because if row/id 1 is deleted, the above code won’t catch it. I’m afraid that you’ll have to use `SELECT` to check for this:

````
SELECT count(id) FROM table WHERE id = 1
````

If the value is 0, then you know you need to create row id 1.

And that’s it. All you need to do is throw this together into a MySQL function (or a php function if you’re not feeling adventurous), and you have the lowest unused primary key all ready for you to put into your `INSERT` line.
