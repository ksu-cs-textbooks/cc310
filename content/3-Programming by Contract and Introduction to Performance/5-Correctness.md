---
title: "Correctness"
weight: 25
pre: "5. "
---
{{% youtube Yc1u0ja3iVY %}}

If we have defined the correct preconditions, postconditions, and invariants for our code, we can then use those to prove that our code correctly performs its intended operation.

In this course, we won't ask you to do any of this yourself, but it is important to understand what is going on in the background and how this process works. We can use the concepts of preconditions and postconditions when grading your code using our Autograder---in fact, that's really how it works!

## Proving Correctness

To prove correctness of a method, we can generally follow this process:

1. Establish (or assume) that the method's preconditions are all true
1. Use the preconditions and the code to demonstrate that any invariants within the code are always true
    1. If the code contains a loop, we can repeat this process for preconditions and postconditions of the loop
1. Use the preconditions and invariants to show that the postcondition is true

Let's do this for our `maximum()` method described on the previous page. Here is the pseudocode once again:

```tex
function MAXIMUM(NUMBERS)
    MAX = NUMBERS[0]
    loop I from 1 to length of NUMBERS
        if NUMBERS[I] > MAX
            MAX = NUMBERS[I]
        end if
    end loop
    return MAX
end function
```

Here are the associated conditions we established as well:

**Method Precondition:** `NUMBERS` is an array containing at least one numerical value, either a floating point or an integer
**Loop Precondition:** `MAX` contains the maximum value stored in `NUMBERS` up to and including index $0$.
**Loop Invariant:** `MAX` contains the maximum value stored in `NUMBERS` up to and including index $I$. 
**Loop Postcondition:** `MAX` contains the maximum value stored in `NUMBERS` up to and including the last index.
**Method Postconditions:** The method returns the maximum value stored in the `NUMBERS` array, and the `NUMBERS` array is not modified by the method

Now that we have that information, we can discuss the _correctness_ of the method.

## A Simple Proof

To begin, we assume that the method's preconditions are true. Therefore, we know that `NUMBERS` is an array containing at least one numerical value. Earlier in this chapter, we learned that we can't assume that the method works if the preconditions are false, so we can always begin our proof by assuming they are true.

Next, we have to use the code as well as the method's preconditions to establish that the loop's preconditions are true. In the code, we see that we set the value of `MAX` equal to the first element in the `NUMBERS` array. So, since there is only that value in the `NUMBERS` array up to and including index $0$, it is easy to say that it is indeed the maximum value. So, we've shown that our loop's precondition is true. 

After that, we have to show that the loop invariant is true after each iteration of the loop. A proper proof would involve a technique called _proof by induction_, which is more advanced than we want to cover in this course. However, a simple way to think about it is to say that the value in `MAX` contains the largest value in the list that we've seen so far. On each loop iteration, we look at one more value. If it is larger than `MAX`, then it becomes the new `MAX` value. Otherwise, we know that the maximum value we've seen so far hasn't changed. So, we can show that our loop invariant is always true after each loop iteration.

Finally, once we reach the end of the loop, we've looked at every element including the last index, and found the `MAX` value, so it is easy to see that our loop postcondition is true.

Then, we can quickly use that loop postcondition to understand that the `MAX` value is really the largest in the `NUMBERS` array, which means that the first part of our method's postcondition is also true.

But wait! What about the second part, that insists that we did not modify the contents of the numbers array? Thankfully, we can quickly look at our code and determine that we are not assigning a value into the array, nor do we call any functions on the array, so it is easy to show that our code has not modified it in any way.

There we go! This is a quick example for how we can use preconditions, postconditions, and invariants to help understand our code and whether it works correctly.

On the next page, we'll learn about _unit testing_ and how we can write our own code to verify that our code works correctly.
