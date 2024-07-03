---
title: "Node and Edge Functions"
weight: 45
pre: "9. "
---
{{< youtube MNoJEn_EvBk  >}}

- `add node`: will add a node to the graph with the given value if our graph still has room. Procedurally, we will try to put the node in the first empty place we find. To do this, we start with `IDX` equal to negative one then loop through all of the indexes of the graphs `nodes` attribute. At each index, we check if that entry is equal to the value we are trying to add. This will check if the value is already in our graph. If there is nothing in that entry and the `IDX` variable is still negative one, then we will set `IDX` equal to that index. We continue looping through the `nodes` attribute until we reach the end. It is possible that there is more than one open space in the `nodes` attribute. Thus, by checking if `IDX` is still negative one we can make sure to put `value` in the first empty spot. Once we finish going through `nodes` we check to see if we ever found an open spot. If `IDX` is still negative one, this would indicate that there was no room. Otherwise, we put `value` into `nodes` at spot `IDX` and increment the size.

``` tex
function ADDNODE(VALUE)
    IDX = -1
    for NODE in NODES
        if NODE is VALUE 
            return NODE's index
        if NODE has no entry and IDX is -1
            IDX = NODE's index
    if IDX is not -1
        add VALUE to NODES at position IDX
        increment SIZE
    return IDX
```

- `remove node`: will remove a node to the graph with the given value if our graph has the node. We will set the node to be empty and remove any edges that may be attached to it. 

``` tex
function REMOVENODE(IDX)
    if IDX is in the range of our indexes 
        if NODES at position IDX is not empty
            set NODES at IDX to be empty
            decrement SIZE by one
            for J in node indexes 
                set EDGES (J,IDX) equal to infinity 
                set EDGES (IDX,J) equal to infinity
            return true
        else
            return false
    else
        return false 
```

- `add edge`: will add an edge with the given weight which goes from the source node to the target node 

``` tex
function ADDEDGE(SOURCE, TARGET, WEIGHT)
    if SOURCE and TARGET are both in the range of our node indexes
        set EDGES(SOURCE, TARGET) equal to WEIGHT
        return true 
    else
        return false
```

- `remove edge`: will remove the edge which goes from the source node to the target node 

``` tex
function REMOVEEDGE(SOURCE, TARGET)
    if SOURCE and TARGET are both in the range of our node indexes
        if EDGES(SOURCE, TARGET) is not equal to infinity
            set EDGES(SOURCE, TARGET) equal to infinity
            return true 
        else
            return false
    else
        return false
```


- `add undirected edge`: will add two edges with the given weight between the two given nodes

``` tex
function ADDUNDIRECTEDEDGE(NODE1, NODE2, WEIGHT)
    RES = ADDEDGE(NODE1, NODE2, WEIGHT)
    RES = RES and ADDEDGE(NODE2, NODE1, WEIGHT)
    return RES
```

- `remove undirected edge`: will remove two edges between the two given nodes. We can utilize the remove edge function on 'NODE1' to 'NODE2' and then on 'NODE2' to 'NODE1'.

``` tex
function REMOVEUNDIRECTEDEDGE(NODE1, NODE2)
    RES = REMOVEEDGE(NODE1, NODE2)
    RES = RES and REMOVEEDGE(NODE2, NODE1)
    return RES
```
