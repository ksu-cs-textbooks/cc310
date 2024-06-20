---
title: "Tree Recursion"
weight: 25
pre: "5. "
---
{{< youtube R6rXXaVx7DU  >}}

In the previous examples we saw recursive functions that call themselves one time within the code. This type of recursion is called _linear recursion_, where head and tail recursion are two specific types of linear recursion.

In this section we will investigate another type of recursion called _tree recursion_, which occurs when a function calls itself two or more times to solve a single problem. To illustrate tree recursion, we will use a simple recursive function `MAX`, which finds the maximum of $N$ elements in an array. To calculate the maximum of $N$ elements we will use the following recursive algorithm.

1. Compute the maximum of the first $N/2$ elements and store in `MAX1`.
1. Compute the maximum of the last $N/2$ elements and store in `MAX2`.
1. Compare `MAX1` and `MAX2` to find the maximum of all elements.

Our process recursively decomposes the problem by searching for the maximum in the first $N/2$ elements and the second $N/2$ elements until we reach the base case. In this problem, the base case is when we either have 1 or 2 elements in the array. If we just have 1, we return that value. If we have 2, we return the larger of those two values. An overview of the process is shown below. 
 
![Tree Recursion](/images/6/6.6.tree.png)
 
The pseudocode for the algorithm is shown below.

```tex
function MAX(VALUES, START, END)
    print "Called MAX with start = " + START + ", end = " + END
    if END – START = 0
        return VALUES[START]
    else if END – START = 1
        if VALUES(START) > VALUES(END)
            return VALUES[START]
        else
            return VALUES[END]
        end if
    else
        MIDDLE = ROUND((END – START) / 2) 
        MAX1 = MAX(VALUES, START, START + MIDDLE – 1)
        MAX2 = MAX(VALUES, START + MIDDLE, END)
        if MAX1 > MAX2
            return MAX1
        else
            return MAX2
        end if
    end if
end function
```

The following block shows the output from the `print` line in the `MAX` function above. The initial call to the function is `MAX(VALUES, 0, 15)`.

```tex
Called MAX with start = 0, end = 7
Called MAX with start = 0, end = 3
Called MAX with start = 0, end = 1
Called MAX with start = 2, end = 3
Called MAX with start = 4, end = 7
Called MAX with start = 4, end = 5
Called MAX with start = 6, end = 7
Called MAX with start = 8, end = 15
Called MAX with start = 8, end = 11
Called MAX with start = 8, end = 9
Called MAX with start = 10, end = 11
Called MAX with start = 12, end = 15
Called MAX with start = 12, end = 13
Called MAX with start = 14, end = 15
```

As you can see, `MAX` decomposes the array each time it is called, resulting in 14 instances of the `MAX` function being called. If we had performed head or tail recursion to compare each value in the array, we would have to have called `MAX` 16 times. While this may not seem like a huge savings, as the value of $N$ grows, so do the savings. 
