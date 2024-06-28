---
title: "Invariants"
weight: 20
pre: "4. "
---
{{< youtube KxNJqvU31oI  >}}

Another concept related to preconditions and postconditions is the _loop invariant_. A loop invariant is a statement should be true after each iteration of a loop, provided the loop's _preconditions_ are all true before the start of the loop. Yes, that's right---we can think of a loop as a miniature method within a method, with its own set of preconditions and postconditions. 

## Example - Maximum

For this example, let's consider a method `maximum(numbers)` that gets an array of numbers as input, and returns the maximum value stored in that list. So, we can start by listing the preconditions of the method:

1. `numbers` is an array containing at least one numerical value, either a floating point or an integer

Thankfully, that one precondition covers all of our bases. Likewise, we can define our postcondition pretty easily as well:

1. The method returns the maximum value stored in the `numbers` array
1. The `numbers` array is not modified by the method

There we go! Hopefully it is easy to see how the preconditions and postconditions help us build a better definition of what operations should be performed by the method.

### Method Pseudocode

Now that we've built our method's preconditions and postconditions, let's quickly write the method in pseudocode so we can see what it would look like.

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

We've seen methods like this several times already, since calculating the maximum value from an array of values is a very common task. This time, however, let's discuss the preconditions, postconditions and invariants of the loop inside of this method.

### Preconditions

First, we can establish an important precondition at the beginning of the loop. In this case, the precondition that best describes the value stored in `MAX` is:

1. `MAX` contains the maximum value stored in `NUMBERS` up to and including index $0$.

In this way, we've directly tied our precondition to the values that exist in the method already, and we've accurately described the value that `MAX` is currently storing. 

{{% notice tip %}}

# Confused?

Don't worry if this doesn't make sense right now - you won't be expected to write your own preconditions and invariants at this point. We're just introducing the concepts so you'll understand how they work when you see them later in the projects in this course

{{% / notice %}}

### Loop Invariant

Next, we can determine what the loop invariant should be. This is a statement that should be true after each iteration of the loop, provided the precondition is true. Usually we want to try and relate it to the precondition somehow, and how it changes after each iteration of the loop. So, let's consider the following loop invariant:

1. `MAX` contains the maximum value stored in `NUMBERS` up to and including index $I$. 

Hmm, that's almost exactly the same as the precondition, isn't it? That's what we're going for here. In this way, we can easily describe what the loop does after each iteration based on how it updates the value in `MAX`, keeping the loop invariant true. We call that "maintaining the loop invariant."

### Postcondition

Finally, we can define the postcondition of the loop. This is pretty simple, since it is the same as the loop invariant, but this time we can say that `I` is equal to the end of the loop. So, our postcondition is simply:

1. `MAX` contains the maximum value stored in `NUMBERS` up to and including the last index. 

That's all there is to it! By defining a precondition, invariant, and postcondition for our loop, we can very accurately describe exactly what that loop should do. On the next page, we'll see how we can put all of those together to show that our method works correctly.
