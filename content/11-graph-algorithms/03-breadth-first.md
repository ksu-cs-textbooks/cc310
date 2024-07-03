---
title: "Breadth First"
weight: 15
pre: "3. "
---
{{< youtube FViSRGbGn54  >}}

[Video Slides](https://core.cs.ksu.edu/4-cc315/08-graph-traversal/03-graph-traversals-bfs-slides/#/)

We can also perform a breadth first traversal either iteratively or recursively. As with the depth first traversal, we will define it iteratively. 

In the iterative algorithm, we initialize an empty queue and an empty set. Like depth first traversal, the set will track which nodes we have discovered. We now use a queue to track which node we will search next. 

{{% notice info %}}

Recall that a queue is a 'First In First Out' (FIFO) structure. Based on this, the breadth first traversal will traverse a nodes siblings before its descendants.

{{% / notice %}}

Again, we must pick a starting node; this can be an arbitrary node in our graph. We add the starting node to our queue and the set of discovered nodes. We start a while loop to go through the queue which we will be enqueue  and dequeue from. We get the first element of the queue, then get the neighbors of the current node. We loop through each edge adding the neighbor to the discovered set and the queue if it has not already been discovered. We continue this process until the queue is empty. 


![BFS Example GIF](images/16/SEARCH_BFS.gif)


``` tex
function BREADTHFIRST(GRAPH,SRC)
    QUEUE = empty queue
    DISCOVERED = empty set
    add SRC to DISCOVERED
    add SRC to QUEUE
    while QUEUE is not empty
        CURR = first element in QUEUE
        NEIGHS = neighbors of CURR
        for EDGE in NEIGHS
            NODE = first entry in EDGE
            if NODE is not in DISCOVERED
                add NODE to DISCOVERED
                append NODE to QUEUE
```

{{% notice info %}}

It is important to remember in these implementations that a stack is used for depth first and a queue is used for a breadth first. The stack, being a LIFO structure, will proceed with the newest entry which will put us farther away from the source. The queue, being a FIFO structure, will proceed with oldest entry which will focus the algorithm more on the adjacent nodes. If we were to use say a queue for a depth first search, we would be traversing neighbors before descendants. 

{{% / notice %}}


