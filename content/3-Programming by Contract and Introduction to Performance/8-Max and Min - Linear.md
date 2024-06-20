---
title: "Max and Min - Linear"
weight: 40
pre: "8. "
---
{{< youtube dByG6Fv9VB4  >}}

Let’s start by considering one number from the list at a time. 

## Base Case

When we have received just one number, this number is both the maximum and the minimum. In the initial state, you have `max` holding the maximum, and `min` holding the minimum. The invariant is the following: 

1. The variable `max` holds the maximum of all the numbers considered so far
2. The variable `min` holds the minimum of all the numbers considered so far

The algorithm is depicted by the following flowchart and pseudocode:

![Min Max Flowchart Base](/images/3/3.9.base.png)

```tex
print "Enter a Number:"
input X
MAX = X
MIN = X
```

## The Next Number

Then, our program will enter a loop to read 10 more numbers from the user. So, we'll need to perform the following process during each iteration of the loop:

1. compare the value in `max` with this new number and update the `max` value if the new number is greater. In this way, the invariant is preserved.
1. compare the value in `min` with this new number and update the `min` value if the new number is smaller. In this way, the invariant is preserved. 

This part of the program is depicted by the following flowchart and pseudocode: 

![Min Max Flowchart Loop](/images/3/3.9.loop.png)

```tex
loop I from 1 to 10
    print "Enter a Number:"
    input X
    if X > MAX
        MAX = X
    end if
    if X < MIN
        MIN = X
    end if
end loop
```
 
After you've considered the second number, you end up in the same situation at the beginning: you have a maximum and a minimum value of the numbers input by the user so far. You have found an **invariant** if you verify that the preconditions before executing an iteration of the loops are the same as the conditions at the end of the loop, known as postconditions:

* Loop preconditions: 
  1. The variable `max` holds the maximum value among all the numbers considered so far
  2. The variable `min` holds the minimum value among all the numbers considered so far
  3. The new input considered is a number
* Loop postconditions: 
  1. The variable `max` holds the maximum value among all the numbers considered so far
  2. The variable `min` holds the minimum value among all the numbers considered so far
* Loop invariant:
  1. The variable `max` holds the maximum value among all the numbers considered so far
  1. The variable `min` holds the minimum value among all the numbers considered so far

You can then generalize the solution for the `n`th input: when you consider the `n`th number, compare it with the values in `max` and `min`, updating them if necessary. In each step, we can show that the invariant holds.  

A full flowchart of this program can be found by clicking the following link:

[Min Max Flowchart](/images/3/3.9.flow.png)

It is helpful to have this diagram available in a second browser tab for review on the next few pages. 
