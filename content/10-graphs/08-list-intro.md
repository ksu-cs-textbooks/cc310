---
title: "Introduction"
weight: 40
pre: "8. "
---

{{< youtube DgN_qmbtK_M  >}}

In the previous module, we introduced graphs and a matrix-based implementation. For this module, we will continue working with graphs and change our implementation to lists. 

## Why Another Implementation?

When using graphs, a lot of situational variation can occur. Some graphs can have a few nodes with many edges, many nodes with few edges, and so on. When we use the matrix implementation, we initialize a matrix with the number of columns and rows equal to the number of nodes. For example, if we have a graph with 20 nodes, our adjacency matrix would have 20 rows and 20 columns, resulting in 400 potential entries. 

First let's look at the implementation and then we will discuss when one may be better than the other. 
