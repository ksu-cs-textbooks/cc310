---
title: "Graph Algorithms"
weight: 35
pre: "7. "
disableMathJax: false
---

### Path Searches

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

- **Time**: The time analysis for the depth first search can be a bit complex. Lines 1 through 5 would execute in near constant time. When we start the while loop on line 6, it is more difficult to analyze how many times this can execute as `STACK` can contain duplicates. In the case that we have a sparse graph, this would be bound by the number of nodes. For a dense graph however, the number of executions would be bound by the number of edges. The code within the while loop would be bound by the number of nodes because of the check that we have not already discovered the node in line 8. If we haven't discovered it, we would take either the logic of lines 8 through 16 or lines 17 through 23 but never both in the same iteration. Both of these blocks are bound by the number of nodes in our graph. Thus the worst case time requirement would be $n^2$.
- **Space**: Depending on the density of our graph, the space required will be linear with respect to the number of nodes or edges. This is due to the fact that `STACK` can contain duplicate nodes. If we have a sparse graph then it will be bound by the number of nodes. If we have a dense graph then the space is bound by the number of edges.
    - `STACK`: linear with respect to the number of edges
    - `DISCOVERED`: linear with respect to the number of nodes
    - `PARENT_MAP`: linear with respect to the number of nodes
    - `CURR`: 1
    - `PATH`: linear with respect to the number of nodes
    - `TRACE`: 1
    - `NEIGHS`: linear with respect to the number of neighbors
    - `EDGE`: 1
    - `NODE`: 1
    
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

- **Time**: The run time expected for breadth first search is a bit more straight forward as `QUEUE` will never have duplicates. Lines 1 through 6 will all execute in constant time. The while loop will occur $n$ times where $n$ is the number of nodes. Based on the logic, either 9-16 will execute or 17-24 will execute. Both of these are bound by the number of nodes in terms of time. Each iteration of the while loop will take $n$ time and we do the while loop $n$ times; thus the running time will be $n^2$.
- **Space**: The space required for BFS will be linear with respect to the number of nodes. We have 5 variables which have size bound by the number of nodes. If the number of nodes doubles, then we expect the amount of space to roughly double. 
    - `QUEUE`: linear with respect to the number of nodes
    - `DISCOVERED`: linear with respect to the number of nodes
    - `PARENT_MAP`: linear with respect to the number of nodes
    - `CURR`: 1
    - `PATH`: linear with respect to the number of nodes
    - `TRACE`: 1
    - `NEIGHS`: linear with respect to the number of nodes
    - `EDGE`: 1
    - `NODE`: 1

### Minimum Spanning Trees

{{< highlight lineNos="true" lineNoStart="1" type="py" >}}
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
{{< /highlight >}}

- **Time**: The time to initialize `MST` would be linear with respect to the number of nodes. Regardless of the graph implementation, inserting nodes is constant time and we would do it for the number of nodes in `GRAPH`. Lines 4-6 would take linear time with respect to the number of nodes. Then lines 9-19 would take linear time with respect to the number of edges as it would execute $e$ times and each operation can be done in constant time, except for searching through the sets and performing set operations, which require $log_2(n)$ time. Thus, Kruskal's algorithm will take time on the order of $e \times log_2(n)$ in the worst case. 

- **Space**:The required space for Kruskal's algorithm is dependent on the implementation of the MST. A matrix graph would require $n^2$ space and a list graph we would require $n+e$ space.
    - `MST`: matrix graph $n^2$ or list graph $n+e$
    - `ALLSETS`: linear with respect to the number of nodes
    - `NODE`: 1
    - `GRAPH NODES`: linear with respect to the number of nodes
    - `SET`: 1
    - `EDGES`: linear with respect to the number of edges
    - `SORTEDEDGES`: linear with respect to the number of edges
    - `SRC`: 1
    - `TAR`: 1
    - `SRCSET`: 1
    - `TARSET`: 1
    - `UNIONSET`: 1

{{< highlight lineNos="true" lineNoStart="1" type="py" >}}
function PRIM(GRAPH, START)
    MST = GRAPH without the edges attribute(s)
    VISITED = empty set
    add START to VISITED
    AVAILEDGES = list of edges where START is the source
    sort AVAILEDGES
    while VISITED is not all of the nodes
        SMLEDGE = smallest edge in AVAILEDGES
        SRC = source of SMLEDGE
        TAR = target of SMLEDGE
        if TAR not in VISITED
            add SMLEDGE to MST as undirected edge
            add TAR to VISITED
            add the edges where TAR is the source to AVAILEDGES
        remove SMLEDGE from AVAILEDGES
        sort AVAILEDGES
    return MST
{{< /highlight >}}

- **Time without Priority Queue**: The time to initialize `MST` would be linear with respect to the number of nodes. Regardless of the graph implementation, inserting nodes is constant time and we would do it for the number of nodes in `GRAPH`. With a matrix graph, setting up `AVAILEDGES` would take linear time with respect to the number of nodes. With a list graph, this would happen in constant time. Then, we need to get the smallest edge from the `AVAILEDGES` list, which would be a linear time operation based on the number of edges, and we must do that once for up to each edge in the graph. So, the worst case running time for Prim's algorithm is $e^2$. (Our implementation is actually a bit slower than this since we sort the list of available edges each time, but that is technically not necessary - our implementation is closer to $e^2 \times log_2(e)$!)
- **Time with Priority Queue**: We do get an improvement when we choose to implement this with a priority queue. For the most part, the performance is the same. Using a priority queue, heapify would optimize the sorting to happen in linear time with respect to the number of elements. In that case, we can reduce the total running time to on the order of $e \times log_2(n)$, which is the same as Kruskal's algorithm. 
- **Space**: The required space for Prim's algorithm is also dependent on the implementation of the MST. A matrix graph would require $n^2$ space and a list graph we would require $n+e$ space. 
    - `MST`: matrix graph $n^2$ or list graph $n+e$
    - `VISITED`: linear with respect to the number of nodes
    - `AVAILEDGES`: linear with respect to the number of edges
    - `SMLEDGE`: 1
    - `SRC`: 1
    - `TAR`: 1


### Shortest Path

{{< highlight lineNos="true" lineNoStart="1" type="py" >}}
DIJKSTRAS(GRAPH, SRC)
   SIZE = size of GRAPH
   DISTS = array with length equal to SIZE
   PREVIOUS = array with length equal to SIZE
   set all of the entries in PREVIOUS to none
   set all of the entries in DISTS to infinity 
   DISTS[SRC] = 0 
   PQ = min-priority queue
   loop IDX starting at 0 up to SIZE
        insert (DISTS[IDX],IDX) into PQ
    while PQ is not empty
        MIN = REMOVE-MIN from PQ
        for NODE in neighbors of MIN
            WEIGHT = graph weight between MIN and NODE
            CALC = DISTS[MIN] + WEIGHT
            if CALC < DISTS[NODE]
                DISTS[NODE] = CALC
                PREVIOUS[NODE] = MIN
                PQIDX = index of NODE in PQ
                PQ decrease-key (PQIDX, CALC)
    return DISTS and PREVIOUS
{{< /highlight >}}

- **Time**: The time required for Dijkstra's algorithm will be $n^2$ in the worst case. We would expect lines 1 through 8 to take constant time. The for loop on line 9 would be bound by the number of nodes. We would expect the for loop on line 13 to be bound by the number of nodes. This for loop will execute each time `PQ` is not empty (line 11), which is bound by the number of nodes. Thus, the block of code starting at 11 will take $n^2$ time to run in the worst case. This means that if we double the number of nodes, then the running time will be quadrupled. The worst case for Dijkstra's algorithm is characterized by being a very dense graph, meaning each node has a lot of neighbors. If the graph is sparse and our priority queue is efficient, we could expect this running time to be more along the lines of $(n + e) \times log_2(n)$, where $e$ is the number of edges. 
- **Space**: The required space for Dijkstra's algorithm will be linear with respect to the number of nodes. We have 4 variables which have linear size with respect to the number of nodes. We say that this is linear because if we were to double the number of nodes, we would roughly double the space requirement. 
    - `SIZE`: 1
    - `DISTS`: linear with respect to the number of nodes
    - `PREVIOUS`: linear with respect to the number of nodes
    - `PQ`: linear with respect to the number of nodes
    - `IDX`: 1
    - `MIN`: 1
    - `NODE`: 1
    - `NEIGHBORS`: linear with respect to the number of nodes
    - `WEIGHT`: 1
    - `CALC`: 1
    - `PQIDX`: 1
