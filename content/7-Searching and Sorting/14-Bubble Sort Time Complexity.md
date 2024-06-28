---
title: "Bubble Sort Time Complexity"
weight: 70
pre: "14. "
disableMathJax: false
---
Once again, let's look at the time complexity of the bubble sort algorithm and see how it compares to selection sort. 

Bubble sort is a bit trickier to analyze than selection sort, because there are really two parts to the algorithm:

1. The number of comparisons, and
2. The number of swaps.

Let's look at each one individually. First, is there a way to reduce the number of comparisons made by this algorithm just by changing the input? As it turns out, there isn't anything we can do to change that based on how it is written. The number of comparisons only depends on the size of the array. In fact, the analysis is exactly the same as selection sort, since each iteration of the outer loop does one fewer comparison. Therefore, we can say that bubble sort has time complexity on the order of $N^2$ time when it comes to comparisons.

What about swaps? This is where it gets a bit tricky. What would be the worst-case input for the bubble sort algorithm, which would result in the largest number of swaps made? 

Consider a case where the input is sorted in descending order. The largest element will be first, and the smallest element will be last. If we want the result to be sorted in ascending order, we would end up making $N - 1$ swaps to get the first element to the end of the array, then $N - 2$ swaps for the second element, and so on. So, once again we end up with the same series as before:

$$
(N – 1) + (N – 2) + ... + 2 + 1.
$$

In the worst-case, we'll also end up doing on the order of $N^2$ swaps, so bubble sort has a time complexity on the order of $N^2$ time when it comes to swaps as well.

## Comparing Selection Sort and Bubble Sort

It seems that both bubble sort and selection sort are in the same order of time complexity, meaning that each one will take roughly the same amount of time to sort the same array. Does that tell us anything about the process of sorting an array?

Here's one way to think about it: what if we decided to compare each element in an array to every other element? How many comparisons would that take? We can use our intuition to know that each element in an array of $N$ elements would require $N – 1$ comparisons, so the total number of comparisons would be $N * (N – 1)$, which is very close to $N^2$.

Of course, once we've compared each element to every other element, we'd know exactly where to place them in a sorted array. One possible conclusion we could make is that there isn't any way to sort an array that runs much faster than an algorithm that runs in the order of $N^2$ time.

Thankfully, that conclusion is incorrect! There are several other sorting algorithms we can use that allow us to sort an array much more quickly than $N^2$ time. Let's take a look at those algorithms and see how they work!
