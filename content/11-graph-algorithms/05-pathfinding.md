---
title: "Pathfinding"
weight: 25
pre: "5. "
---

{{< youtube DKy-q1hWPpQ  >}}

An important application for these traversals is the ability to find a path between two nodes. This has many applications in railroad networks as well as electrical wiring. With some modifications to the traversals, we can determine if electricity can flow from a source to a target. We will modify depth first and breadth first traversals in similar ways.

{{% notice info %}}

There are three cases that can happen when we search for a path between nodes:
- No Path: will return nothing
- One Path: will return the path
- Multiple Paths: will return A path

With these searches, we are not guaranteed to return the same path if there are multiple paths. 

{{% / notice %}}

We will call these Depth First Search (DFS) and Breadth First Search (BFS). In both traversals, we have added the following extra lines: 4, 9-16, and 22 through the end. 

First, we have the addition of `PARENT_MAP` which will be a dictionary to keep track of how we get from one node to another. We will use the convention of having the key be the child and the value be the parent. While we use the terms child and parent, this is not exclusive to trees. 

The ending portion starting at line 22, will add entries to our dictionary. If we haven't already found an edge to `NODE`, then we will add the edge that we are currently on. 

The other addition is the block of code from line 9 to 16. We will enter this `if` block if the node that we are currently at is the target. This means that we have finally found a path from the source node to the target node. The process in this segment of code will backtrack through the path and build the path. 

### Depth-First Search

{{< highlight lineNos="true" lineNoStart="1" type="py" >}}
function DEPTHFIRSTSEARCH(GRAPH,SRC,TAR)
    STACK = empty array
    DISCOVERED = empty set
    PARENT_MAP = empty dictionary
    append SRC to STACK
    while STACK is not empty
        CURR = top of the stack
        if CURR not in DISCOVERED
            if CURR is TAR
                 PATH = empty array
                 TRACE = TAR
                 while TRACE is not SRC
                     append TRACE to PATH
                     set TRACE equal to PARENT_MAP[TRACE]
                 reverse the order of PATH
                 return PATH
            add CURR to DISCOVERED
            NEIGHS = neighbors of CURR
            for EDGE in NEIGHS
                NODE = first entry in EDGE
                append NODE to STACK
                if PARENT_MAP does not have key NODE
                    in the PARENT_MAP dictionary set key NODE with value CURR
    return nothing
{{< /highlight >}}

### Depth-First Search Example

![DFS Example GIF](images/16/DFS.gif)

### Breadth-First Search

{{< highlight lineNos="true" lineNoStart="1" type="py" >}}
function BREADTHFIRSTSEARCH(GRAPH,SRC,TAR)
    QUEUE = empty queue
    DISCOVERED = empty set
    PARENT_MAP = empty dictionary
    add SRC to DISCOVERED
    add SRC to QUEUE
    while QUEUE is not empty
        CURR = first element in QUEUE
        if CURR is TAR 
            PATH = empty list 
            TRACE = TAR
            while TRACE is not SRC
                    append TRACE to PATH
                    set TRACE equal to PARENT_MAP[TRACE]
                reverse the order of PATH
                return PATH
        NEIGHS = neighbors of CURR
        for EDGE in NEIGHS
            NODE = first entry in EDGE
            if NODE is not in DISCOVERED
                add NODE to DISCOVERED
                if PARENT_MAP does not have key NODE
                    in the PARENT_MAP dictionary set key NODE with value CURR
                append NODE to QUEUE
    return nothing
{{< /highlight >}}

### Breadth-First Search Example

![BFS Example GIF](images/16/BFS.gif)
