---
title: "Kruskal"
weight: 45
pre: "9. "
---

{{< youtube av-r-orP56g  >}}

As graphs get larger, it is important to go about finding the MST in a methodical way. In the mid 1950's, there was a desire to form an algorithmic approach for solving the 'traveling salesperson' problem^[We will describe this problem in a future section of this module]. Joseph Kruskal first published this algorithm in 1956 in the Proceedings of the American Mathematical Society[^1]. The algorithms prior to this were, as Kruskal said, "unnecessarily elaborate" thus the need for a more succinct algorithm arose. 

[^1]: https://www.ams.org/journals/proc/1956-007-01/S0002-9939-1956-0078686-7/S0002-9939-1956-0078686-7.pdf

### Algorithm

In his original work, Kruskal outlined three different yet similar algorithms to finding a minimum spanning tree. The `Kruskal Algorithm` that we use is as follows: 

1. Start with only the nodes of the graph and an empty set for the edges
1. Order the edges based on weight
1. Make each node their own set
1. Go through the edges in ascending order
1. If nodes `u` and `v` are connected by the edge and they are not in the same set yet, then join the two sets and add the edge to your set of edges


### Starting Graph

![Kruskal Example Start](images/16/315_9_Lex.svg)


![Kruskal Example GIF](images/16/kruskal.gif)

### Resulting MST

![Kruskal Example Result](images/16/315_9_Kdone.svg)

### Pseudocode

``` tex
function KRUSKAL(GRAPH)
    MST = GRAPH without the edges attribute(s)
    ALLSETS = an empty list which will contain the sets
    for NODE in GRAPH NODES
        SET = a set with element NODE
        add SET to ALLSETS
    EDGES = list of GRAPH's edges
    SORTEDEDGES = EDGES sorted by edge weight, smallest to largest
    for EDGE in SORTEDEDGES
        SRC = source node of EDGE
        TAR = target node of EDGE
        SRCSET = the set from SETS in which SRC is contained
        TARSET = the set form SETS in which TAR is contained
        if SRCSET not equal TARSET
            UNIONSET = SRCSET union TARSET
            add UNIONSET to ALLSETS
            remove SRCSET from ALLSETS
            remove TARSET from ALLSETS
            add EDGE to MST as undirected edge
    return MST
```
