---
layout: post
title:  "Mocking in phpunit"
date:   2014-01-10 00:00:00 +0000
categories: blog
tags: development
---
To test a class in PHPUnit, it's easier if you use dependency injection which enables you to mock other classes that
we aren't interested in testing (such as your database layer). So for example, instead of writing code like this to
test a made-up User class:

```
class User() {
    private $db;

    function __construct()
    {
        $this->db = new Database;
    }

    function getUserData()
    {
        return $this->db->getUserData();
    }
}

$user = new User();
```

We can pass in the database class instead:

```
class User() {
    private $db;

    function __construct($db) {
        $this->db = $db;
    }

    function getUserById($userid) {
        return $this->db->getUserData($userid);
    }
}

$db = new Database; $user = new User($db);
```

This means that we can mock the Database object when we're testing the User class, and pass the former into the latter.
We do this as PHPUnit won't override the new keyword.

In PHPUnit, it's a case of creating the class but in place of using the new keyword we use a slightly longer one instead:

```
$mockDb = $this->getMock( 'Database', array('getUserData') );
$mockDb->expects($this->any())
                      ->method('getUserData')
                      ->with('joebloggs')
                      ->will($this->returnValue(
                          array('userid' => 'joebloggs', 'name' => 'Joe Bloggs')
                 );

$user = new User($mockDb);
$this->assertEquals( $user->getUserById('joebloggs'), array('joebloggs', 'Joe Bloggs') )
```

In a nutshell, those two commands says what the class should be, and what the method should expect and return
respectively. To break down what each bit of the two commands do:


 * `getMock()` is saying mock the class given in the 1st parameter, and we want to return given values for the methods
 given in the array in the 2nd parameter

 * The second command has a bit more too it. `expects($this->any())` will mean that it doesn't matter whether the
 method gets called or not: changing it to `expects($this->once())` will mean that if the method isn't called (or is
 called more than once) the test will fail

 * `with()` is the parameters that you should expect to be passed in (which is a good way to check that the parameters
 that's being passed into a particular method are sensible), and `will($this->returnValue())` is what you want to give as
 the known return value, for when you do your test

Of course, there's much more you can do with PHPUnit mocking. The documentation is a pretty good start to find out what else is there.
