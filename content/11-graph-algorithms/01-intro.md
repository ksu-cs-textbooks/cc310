---
title: "Introduction"
weight: 5
pre: "1. "
---
{{< youtube rGiEVQE1hR4  >}}

In the previous modules, we have introduced graphs and two implementations. This module will cover the traversals through graphs as well as path search techniques. 

## Motivation

As we have discussed previously, graphs can have many applications. Based on that, there are many things that we may want to infer from graphs. For example, if we have a graph that depicts a railroad or electrical network, we could determine what maximum flow of the network. The standard approach for this task is the [Ford-Fulkerson Algorithm](https://www.geeksforgeeks.org/ford-fulkerson-algorithm-for-maximum-flow-problem/). In short, given a graph with edge weights that represent capacities the algorithm will determine the maximum flow throughout the graph. 

From the matrix graph module, we used the following distribution network as an example. 

![Sample Distribution Network](images/15/distribution-3.svg)

Conceptually, we would want to determine the maximum number of units that could leave the distribution center without having excess laying around stores. Using the maximum flow algorithm, we would determine that the maximum number of units would be 15.

![Max Flow](images/16/distribution-3MAX.svg)

The driving force in the Ford-Fulkerson algorithm, as well as other maximum flow algorithms, is the ability to find a path from a source to a target. Specifically, these algorithms use breadth first and depth first searches to discover possible paths. 

## Searching

To get to introducing the searches, we will first discuss the basis of them. Those are the depth first traversal and the breadth first traversal. We will outline the premise of these traversals and then discuss how we can modify their algorithms for various tasks, such as path searches. 

We can perform these traversals on any type of graph. Conceptually, it will help to have a tree-like structure in mind to differentiate between depth first and breadth first. 

![Breadth VS Depth](images/16/8search_breadthVSdepth.svg)
