---
title: "Dense VS Sparse"
weight: 50
pre: "10. "
---

{{< youtube y4bCalShe_Y  >}}

When considering which implementation to use, we need to consider the connectivity in our graph. The terms that we use to describe the connectedness are **dense** and **sparse**.

- `Dense Graph`: A dense graph is a graph in which there is a large number of edges. Typically in a dense graph, the number of edges is close to the maximum number of edges. 
- `Sparse Graph`: A sparse graph is a graph in which there is a small number of edges. In this case the number of edges is considerably less than the maximum number of edges. 

{{% notice info %}}

Intuitively, we can think of dense and sparse in terms of populations. For example, if 100 people lived in a city block, we can consider that to be densely populated. If 100 people lived in 100 square miles we can consider that to be sparsely populated. 

{{% / notice %}}

Let's look at some motivating examples to get an idea of how the different structures will handle these cases. 

## Dense

The following is a dense graph. In this case, our graph does have the maximum number of edges. This means that every node is connected to every other node including itself.

![Dense Graph](images/15/dense_graph.svg)
![Dense Graph as Matrix](images/15/dense_matrix.svg)
![Dense Graph as List](images/15/dense_list.svg)

## Sparse 

The following is a sparse graph. 

![Sparse Graph](images/15/sparse_graph.svg)
![Sparse Graph as Matrix](images/15/sparse_matrix.svg)
![Sparse Graph as List](images/15/sparse_list.svg)



List or Matrix?
---

For dense graphs, the matrix representation will have better qualities as we are already setting aside space for the maximum number of edges. Sparse graphs are better represented in the list representation. 

When we initialize the matrix implementation, we initialize the `nodes` attribute to have dimension equal to the capacity of the graph. The `edges` attribute is initialized to be a square matrix with dimension equal to capacity by capacity. Thus, if we have a sparse matrix, we are representing a lot of non-existent edges.

When we initialize the list implementation, we just have the `nodes` attribute which has dimension equal to the capacity and each node tracks its own edges. If we have a dense matrix and we are searching for an edge, we must loop through each edge from the target node to see if the edge exists. In the matrix representation, we can access that edge directly. 


{{% notice info %}}

If the proportion of edges to the maximum number of edges is greater than 1/64, then the matrix representation is better in terms of space. 

{{% / notice %}}
