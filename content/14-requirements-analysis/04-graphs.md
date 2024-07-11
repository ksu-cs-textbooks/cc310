---
title: "Graphs"
weight: 20
pre: "4. "
---

Graphs are a good data structure for relational data. This would include data in which elements can have some sort of similarity or distance defined between those elements. This measure of similarity between elements can be defined as realistically or abstractly as needed for the data set. The distance can be as simple as listing neighbors or adjacent elements. 

### Graphs

Graphs are multidimensional data structures that can represent many different types of data using nodes and edges. We can have graphs that are weighted and/or directed and we have introduced two ways we can represent graphs:

#### Matrix Graphs

The first implementation of graphs that we looked at were matrix graphs. In this implementation, we had an array for the nodes and a two dimensional array for all of the possible edges. 

#### List Graphs

The second implementation of graphs were list graphs. For this implementation, we had a single array of graph node objects where the graph node objects tracked their own edges.

Recall that we discussed sparse and dense graphs. Matrix graphs are better for dense graphs since a majority of the elements in the two dimensional array of edges will be filled. A great example of a dense graph would be relationships in a small community, where each person is connected to each other person in some way. 

List graphs are better for sparse graphs, since each node only needs to store the outgoing edges it is connected to. This eliminates a large amount of the overhead that would be present in a matrix graph if there were thousands of nodes and each node was only connected to a few other nodes. A great example of a sparse graph would be a larger social network such as Facebook. Facebook has over a billion users, but each user has on average only a few hundred connections. So, it is much easier to store a list of those few hundred connections instead of a two dimensional matrix that has over one quintillion ($10^{18}$) elements.

In the next chapter, we will discuss the specific implications of using one or the other. However, in our requirement analysis it is important to take this into consideration. If we have relational data where many elements are considered to be connected to many other elements, then a matrix graph will be preferred. If the elements of our data set are infrequently connected, then a list graph is the better choice. 
