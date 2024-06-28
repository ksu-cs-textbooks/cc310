---
title: "Sorting"
weight: 40
pre: "8. "
disableMathJax: false
---
Sorting is the process we use to organize an ordered container in a way that we understand what the ordering of the values represents. Recall that an ordered container just enforces an ordering between values, but that ordering may appear to be random. By sorting an ordered container, we can enforce a specific ordering on the elements in the container, allowing us to more quickly find specific elements as we'll see later in this chapter. 

## Ascending and Descending Order

In most cases, we sort values in either ascending or descending order. Ascending order means that the smallest value will be first, and then each value will get progressively larger until the largest value, which is at the end of the container. Descending order is the opposite---the largest value will be first, and then values will get progressively smaller until the smallest value is last. 

We can also define this mathematically. Assume that we have a container called `array` and two indexes in that container, `a` and `b`. If the container is sorted in ascending order, we would say that if `a` is less than `b` (that is, the element at index `a` comes before the element at index `b`), then the element at index `a` is less than or equal to the element at index `b`. More succinctly:

$$
a < b \implies \text{array}[a] \leq \text{array}[b]
$$

Likewise, if the container is sorted in descending order, we would know that if `a` is less than `b`, then the element at index `a` would be greater than or equal to the element at index `b`. Or:

$$
a < b \implies \text{array}[a] \geq \text{array}[b]
$$

These facts will be important later when we discuss the precondition, postconditions, and loop invariants of algorithms in this section. 

## Sorting Algorithms
To sort a collection of data, we can use one of many sorting algorithms to perform that action. While there are many different algorithms out there for sorting, there are a few commonly used algorithms for this process, each one with its own pros, cons, and time complexity. These algorithms are studied extensively by programmers, and nearly every programmer learns how to write and use these algorithms as part of their learning process. In this module, we'll introduce you to the 4 most commonly used sorting algorithms:

1. Selection Sort,
2. Bubble Sort,
3. Merge Sort, and
4. Quicksort.
