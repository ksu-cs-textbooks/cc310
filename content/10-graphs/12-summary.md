---
title: "Summary"
weight: 60
pre: "12. "
---

In this module, we have introduced the graph data structure. We also looked at how we would implement a graph using a matrix representation. We introduced the following new concepts in this module: 

- `Directed Graphs`: A directed graph is a graph that has a direction associated with each edge. The flat end of the arrow will represent the origin and the arrowhead will represent the destination. If an edge has no arrowheads, then it is assumed that we can traverse both directions. 

- `Edges`: Edges are the connection between two nodes. Depending on the data, edges can represent physical distance, films, cost, and much more. 
    - `Adjacent`: Node A and node B are said to be adjacent if there is an edge from node A to node B. 
    - `Neighbors`: The neighbors of a node are nodes which are adjacent to the node. 
    - `Undirected Edge`: An undirected edge is an edge which has no defined orientation (IE no arrowheads). If node A and node B are connected via an undirected edge then we say node A is adjacent to node B and node B is adjacent to node A.

- `Loops`: Loops are edges which connect a node to itself.

- `Nodes`: Node is the general term for a structure which contains an item. 
    - `Size`: The size of a graph is the number of nodes.
    - `Capacity`: The capacity of a graph is the maximum number of nodes. 

- `Weighted Graphs`: A weighted graph is a graph which has weights associated with the edges. These weights will quantify the  relationships so they can represent dollars, minutes, miles, and many other factors which our data may depend on. 

## Matrix Representation

Graphs can be represented using a matrix of edges between nodes.

![Example 1](images/15/graphA.svg)

## List Representation

In this module, we also introduced a new way to store the graph data structure. Thus, we now have two ways to work with graphs, in lists and in matrices: 

![List Representation for Example 1](images/15/graphA_list_rep.svg)

While these methods show the same information, there are cases when one way may be more desirable than the other. 

We discussed how a sparse graph is better suited for a list representation and a dense graph is better suited for a matrix representation. We also touched on how working with the edges in a list representation can add complexity to our edge functions. If we are needing to access edge weights or update edges frequently, a matrix representation would be a good choice -- especially if we have a lot of nodes. 