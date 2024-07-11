---
title: "Introduction"
weight: 5
pre: "1. "
---

{{< youtube QEFyC0gGc_E  >}}

The next data structure we will cover is heaps. The heaps discussed in this course are not to be confused with heaps which refer to garbage collection in certain coding languages. Heaps are good for situations were we will need to frequently access and update the highest (or lowest) priority item in a set. For example, heaps are a good data structure to use in Prim's algorithm. In Prim's algorithm, we repeatedly got the smallest edge, removed the smallest edge, and then added to and sorted the list of edges. 

### Heap Properties

A heap is an array which we can view as an unsorted binary tree. This tree must have the following properties:
1. Each node has at most two children.
1. If there are nodes in level `i` of the tree, then level `i-1` is full. Below we have an example of how this property has been broken. Level two is not full but there are nodes on level three.
![](images/17/Mod10_ex_full_level.svg)
1. The nodes of the last level are as far left as possible. Below we have an example of how this property has been broken. 

![](images/17/Mod10_ex_left.svg)

{{% notice info %}}

As a consequence of the above properties, the following is true as well: Only one node can have one child, all other nodes will have zero or two children. Try to construct a counterexample to see what we mean! 

{{% / notice %}}

### Types of Heaps

There are two main types of heaps, the max-heap and the min-heap. Depending on the element we want to access we may use one or the other. 

A **max-heap** is a heap such that the parent node is greater than or equal to the children. For example, if we are using a heap to track work flow,we would want to use a max-heap. In this case, the highest priority element will always be the root of the tree. 

A **min-heap** is a heap such that the parent node is less than or equal to the children. This is the opposite of the max-heap. The root of this heap will be the item with the lowest priority. A min-heap may feel unnatural at first, however, this is ideal for greedy algorithms such as Prim's algorithm. We are frequently getting the smallest edge. 
