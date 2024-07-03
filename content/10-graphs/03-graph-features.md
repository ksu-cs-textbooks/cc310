---
title: "Graph Features"
weight: 15
pre: "3. "
---

{{< youtube F_mNd-CIFpc  >}}

While trees are a type of graph, graphs can have more functionality than trees. For example, recall that to be a single tree, there could be no disconnected pieces. 

- `Connectedness`: Graphs do not require being fully connected. There can be disconnected portions within a graph. For example, the following graph shows all of the students in a sophomore biology class. There is an edge between two student nodes if they are Facebook friends. 

![Friends Group](images/15/friends.svg)

Graphs can also have loops. In a tree, this would be like a node being its own parent, which is not an allowable condition. 

- `Loops`: Loops are edges which connect a node to itself. These can be useful in depicting graphs that show control flow in programming. In this example, node A is connected to node B and node A is connected to itself. 

![With a Loop](images/15/loop2.svg)
