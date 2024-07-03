---
title: "Limitations"
weight: 20
pre: "4. "
---

{{< youtube sSz7UDs0cH8  >}}

When introducing graphs, we discussed how the components of a graph didn't have to all be connected. If our goal is to visit each node, like in the searches, then we will need to perform the search from every node. 

For example, the graph below has two separate components. Lets walk through which nodes we will discover by calling the traversals from each node. 

![Disconnected Graph](images/16/8search_dis.svg)

| Start |  Visited (in alphabetical order) | 
| --- | --- |
| A | {A, D, H} | 
| B | {B, E, H, I} |  
| C | \{C\} |  
| D | \{D\} |  
| E | {E, H, I} |  
| F | {C, F} |  
| G | {C, G} |  
| H | \{H\} |  
| I | \{I\} |  
| J | {C, F, G, J} |  

In this example, we would need to call either traversal on nodes A, B and J in order to visit all of the nodes. 
