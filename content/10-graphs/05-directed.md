---
title: "Directed Graphs"
weight: 25
pre: "5. "
---

{{< youtube f7qyV9XOwzA  >}}

A **directed** graph is a graph that has a direction associated with each edge. For example, trees are a directed graph. The edge orientation will imply a fixed direction that we can move about nodes. As with trees, the flat end of the arrow will represent the origin and the arrowhead will represent the destination. If an edge has no arrowheads, then it is assumed that we can traverse both directions. 

In the following graph, we have an example distribution network where each store ends up with 5 units in its possession. For example, nine units go from the distribution center to Store A. The distribution center will never receive product from stores as it has no incoming edges. 

![Sample Distribution Network](images/15/distribution-3.svg)

Unlike trees, directed graphs can have nodes with multiple incoming edges. We can see an example of this at Store B. The distribution center and Store A both send units to Store B. 

{{% notice info %}}

In directed graphs, we must be cautious on how we define **adjacent**. For the following, we would say that the source is adjacent to the target. However, the target is not adjacent to the source. 

![Source and Target Example](images/15/src_tar_ex.svg)

Formally, node A and node B are said to be adjacent if there is an edge from node A to node B. 
{{% / notice %}}


When discussing directed graphs, we must also talk about undirected graphs. An **undirected** graph is a graph in which none of the edges have an orientation. If there is at least one directed edge, then it is considered a directed graph.

- `Undirected Edge`: An undirected edge is an edge which has no defined orientation (IE no arrowheads) which implies that we can traverse in either direction. If node A and node B are connected via an undirected edge then we say node A is adjacent to node B and node B is adjacent to node A.

{{% notice info %}}

For the following undirected edge, we would say that the source is adjacent to the target and the target is adjacent to the source. 

![Source and Target Example](images/15/undirected_edge.svg)

{{% / notice %}}


{{% notice info %}}

Graph types and appearances can vary wildly. We are not limited to just weighted/unweighted or directed/undirected. We can also have combinations of weighted and directed. 

{{% / notice %}}
