---
title: "Selection Sort Time Complexity"
weight: 55
pre: "11. "
---
Let's look at the time complexity of the selection sort algorithm, just so we can get a feel for how much time this operation takes. 

First, we must determine if there is a worst-case input for selection sort. Can we think of any particular input which would require more steps to complete? 

In this case, each iteration of selection sort will look at the same number of elements, no matter what they are. So there isn't a particular input that would be considered worst-case. We can proceed with just the general case. 

In each iteration of the algorithm we need to search for the minimum value of the remaining elements in the container. If the container has $N$ elements, we would follow the steps below.

1. The first time we need to find the minimum among $N$ elements. This will take $N$ comparisons assuming the element are compared one by one with the minimum.
1. The second time we need to find the minimum among $N - 1$ elements. This will take $N - 1$ comparisons.
1. The third time we need to find the minimum among $N - 2$ elements. This will take $N - 2$ comparisons.
1. ... and so on.

This process continues until we have sorted all of the elements in the array. The number of steps will be:

$$
N + (N – 1) + (N – 2) + … + 2 + 1
$$

While it takes a bit of math to figure out exactly what that means, we can use some intuition to determine an approximate value. For example we could pair up the values like this:

$$
N + [(N – 1) + 1] + [(N – 2) + 2] + ...
$$

When we do that, we'll see that we can create around $N / 2$ pairs, each one with the value of $N$. So a rough approximation of this value is $N * (N / 2)$, which is $N^2 / 2$. When analyzing time complexity, we would say that this is "on the order of $N^2$" time. Put another way, if the size of $N$ doubles, we would expect the number of steps to go up by a factor of $4$, since $(2 * N)^2 = 4N$. 

Later on, we'll come back to this and compare the time complexity of each sorting algorithm and searching algorithm to see how they stack up against each other.
