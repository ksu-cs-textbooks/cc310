---
title: "Node and Edge Functions"
weight: 30
pre: "6. "
---
- `add node`: will add a node to the graph with the given value if our graph still has room. Finding a location for the node will be the same procedure as the matrix graph. If we find an open spot to add the node, we will instantiate a new graph node and insert it into the `nodes` attribute.

``` tex
function ADDNODE(VALUE)
    IDX = -1
    for NODE in NODES
        if NODE is VALUE 
            return NODE's index
        if NODE has no entry and IDX is -1
            IDX = NODE's index
    if IDX is not -1
        NEWNODE = graph node with VALUE and IDX for input
        add NEWNODE to NODES at position IDX
        increment SIZE
    return IDX
```

- `remove node`: will remove a node to the graph with the given value if our graph has the node. We will set the node to be empty. When we set the node to be empty, we clear all of the outgoing edges, so we just need to loop through the other nodes removing any possible incoming edges. 

``` tex
function REMOVENODE(IDX)
    if IDX is in the range of our indexes 
        if NODES at position IDX is not empty
            set NODES at IDX to be empty
            decrement SIZE by one
            for NODE in NODES
                if NODE has no entry
                    from NODE call the graph node REMOVEEDGE function on IDX
            return true
        else
            return false
    else
        return false 
```

- `add edge`: will add an edge with the given weight which goes from the source node to the target node 

``` tex
function ADDEDGE(SRC, TAR, WEIGHT)
    if SOURCE and TARGET are both in the range of our node indexes
        SRCNODE = the node at index SRC of the NODES attribute
        if SRCNODE is not empty
            from SRCNODE call the graph node ADDEDGE with TAR and WEIGHT as input
            return true 
        else
            return false
    else
        return false
```

- `remove edge`: will remove the edge which goes from the source node to the target node 

``` tex
function REMOVEEDGE(SOURCE, TARGET)
    if SOURCE and TARGET are both in the range of our node indexes
        SRCNODE = the node at index SRC of the NODES attribute
        if SRCNODE has no entry
            RET = SRCNODE call the graph node REMOVEEDGE with TAR as input
            return RET 
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

- `remove undirected edge`: will remove two edges between the two given nodes. 

``` tex
function REMOVEUNDIRECTEDEDGE(NODE1, NODE2)
    RES = REMOVEEDGE(NODE1, NODE2)
    RES = RES and REMOVEEDGE(NODE2, NODE1)
    return RES
```
