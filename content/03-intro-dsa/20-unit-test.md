---
title: "Unit Testing"
weight: 100
pre: "20. "
---

Once we've written a program, how can we verify that it works correctly? There are many ways to do this, but one of the most common is _unit testing_.

## Unit Testing

Unit testing a program involves writing code that actually runs the program and verifies that it works correctly. In addition, many unit tests will also check that the program produces appropriate errors when given bad input, or even that it won't crash when given invalid input. 

For example, a simple unit test for the `maximum()` method would be:

```tex
function MAXIMUMTEST()
    ARRAY = new array[5]
    ARRAY[0] = 5
    ARRAY[1] = 25
    ARRAY[2] = 10
    ARRAY[3] = 15
    ARRAY[4] = 0
    RESULT = MAXIMUM(ARRAY)
    if RESULT == 25:
        print "Test Passed"
    end if
end function
```

This code will simply create an array that we know the maximum value of, and then confirm that our own `maximum()` method will find the correct result.

Of course, this is a very simplistic unit test, and it would take several more unit tests to fully confirm that the `maximum()` method works completely correctly. 

However, it is important to understand how this test relates to the preconditions and postconditions that were established on previous pages. Here, the unit tests creates a variable `ARRAY` which is an array of at least one numerical value. Therefore, it has met the preconditions for the `maximum()` method, so we can assume that if `maximum()` is written correctly, then the postconditions will be true once it is has executed. This is the key assumption behind unit tests.

{{% notice tip "Why Does This Matter?" %}}

In this course, you will be asked to build several data structures and implement algorithms that use those data structures. In the assignment descriptions, we may describe these methods using the preconditions and postconditions applied to them. Similarly, we'll learn about _structural invariants_ of data structures, which help us ensure that your data structures are always valid.

Then, to grade your work, we use an autograder that contains several unit tests. Those unit tests are used to confirm that you code works correctly, and they do so by providing input that either satisfies the preconditions, meaning that the test expects that the postconditions will be true, or by providing invalid input and testing how your code reacts to those situations.

You'll see these concepts throughout this course, so it is important to be familiar with them now. 

{{% / notice %}}
