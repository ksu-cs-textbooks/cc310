---
title: "Searching"
weight: 5
pre: "1. "
---
In this course, we are learning about many different ways we can store data in our programs, using arrays, queues, stacks, lists, maps, and more. We've already covered a few of these data structures, and we'll learn about the others in upcoming modules. Before we get there, we should also look at a couple of the most important operations we can perform on those data structures. 

Consider the classic example of a data structure containing information about students in a school. In the simplest case, we could use an array to store objects created from a `Student` class, each one representing a single student in the school. 

As we've seen before, we can easily create those objects and store them in our array. We can even iterate through the array to find the maximum age or minimum GPA of all the students in our school. 
However, what if we want to just find a single student's information? To do that, we'll need to discuss one of the most commonly used data structure operations: searching.

## What is Searching?

Searching typically involves finding a piece of information, or a value stored in a data structure or calculated within a specific domain. For example, we might want to find out if a specific word is found in an array of character strings. We might also want to find an integer that meets a specific criterion, such as finding an integer that is the sum of the two preceding integers. For this module, we will focus on finding values in data structures. 

In general, we can search for 

1. a specific value,
1. a sequence of values, or
1. values with specific properties such as the minimum or maximum value.

The data structure can be thought of more generally as a container, which can be 

1. one dimensional, such as a list or a one-dimensional array,
1. multi-dimensional, such as a two-dimensional array or a matrix, or
1. a problem-specific data structure.

For the examples in this module, we'll generally use a simple finite array as our container. However, it shouldn't be too difficult to figure out how to expand these examples to work with a larger variety of data structures. In fact, as we introduce more complex data structures in this course, we'll keep revisiting the concept of searching and see how it applies to the new structure. 

In general, containers can be either ordered or unordered. In many cases, we may also use the term _sorted_ to refer to an ordered container, but technically an ordered container just enforces _an_ ordering on values, but they may not be in a sorted order. As long as we understand what the ordering is, we can use that to our advantage, as we'll see later. 

Searches in an unordered container generally require a _linear search_, where every value in the container must be compared against our search value. On the other hand, search algorithms on ordered containers can take advantage of this ordering to make their searches more efficient. A good example of this is _binary search_. Let's begin by looking at the simplest case, linear search. 
