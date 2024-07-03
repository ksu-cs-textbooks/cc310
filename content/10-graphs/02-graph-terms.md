---
title: "Terms I"
weight: 10
pre: "2. "
---

{{< youtube QIX78W3GUpc  >}}


We will discuss some of the basic terminology associated with graphs. Some of this vocabulary should feel familiar from the trees section; trees are a specific type of graph!

- `Nodes`: Node is the general term for a structure which contains an item. 
    - `Size`: The size of a graph is the number of nodes.
    - `Capacity`: The capacity of a graph is the maximum number of nodes. 

{{% notice info %}}

**Nodes** can be, but are not limited to the following examples:
    - physical locations (IE Manhattan, Topeka, Salina),
    - computer components (IE CPU, GPU, RAM), or 
    - people (IE Kevin Bacon, Laurence Fishburne, Emma Stone)
    
{{% / notice %}}

- `Edges`: Edges are the connection between two nodes. Depending on the data, edges can represent physical distance, films, cost, and much more. 
    - `Adjacent`: Node A and node B are said to be adjacent if there is an edge from node A to node B. 
    - `Neighbors`: The neighbors of a node are nodes which are adjacent to the node. 
    
{{% notice info %}}

**Edges** can be, but are not limited to:
    - physical distances, like the distance between cities or wiring between computer components,
    - cost, like bus fares, and 
    - films, like the Six Degrees of Kevin Bacon example
    
{{% / notice %}}
    
    
- `Cycles`: A cycle is a path where the first and last node are the only repeated nodes. More explicitly, this means that we start at node A and are able to end up back at node A.
    
## Example

For example, we can translate the [Amtrak Train Station Connections](https://www.amtrak.com/content/dam/projects/dotcom/english/public/documents/Maps/Amtrak-System-Map-1018.pdf) into a graph where the edges represent direct train station connections. 

![Amtrak Train Graph](images/15/amtrak.svg)[^1]

[^1]: Generated using the Amtrak system map from 2018. This graph does not include all stations or connections.

Within this context, we could say that Little Rock and Fort Worth are `adjacent`. The `neighbors` of San Antonio are Fort Worth, Los Angeles, and New Orleans. The Amtrak Train Graph has multiple `cycles`. One of these is `Kansas City -> St. Louis -> Chicago -> Kansas City`. 


