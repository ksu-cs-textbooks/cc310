---
title: "MyTree Recursive II"
weight: 35
pre: "7. "
---


### Determine relationships (Ancestor, Descendant, Sibling)

We can determine many relationships within the tree. For example, given a node is it an ancestor of another node, a descendant, or a sibling? 

{{< youtube hr73fsl8RzM  >}}

##### Is Ancestor?
For this function, we are asking: is this node an ancestor of the current instance? In this implementation, we will start at our instance and **work down** through the tree trying to find the node in question. With that in mind, we can define this process recursively:
- Base case: we are at the node in question, so return true OR we are at a leaf so return false. 
- Recursive case: run the method from each of the children of the node.

```tex
function ISANCESTOR(TREE)
    if at TREE
        return true
    else if at LEAF
        return false
    else 
        for CHILD in CHILDREN
            FOUND = CHILD.ISANCESTOR(TREE)
            if FOUND
                return true
        return false
end function
```

##### Is Descendant?
For this function, we are asking: is this node a descendant of the current instance? In this implementation, we will start at our instance and **work up** through the tree trying to find the node in question. With that in mind, we can define this process recursively:
- Base case: we are at the node in question, so return true OR we are at the root so return false. 
- Recursive case: run the method from the parent of the node. 

```tex
function ISDESCENDANT(TREE)
    if at TREE
        return true
    else if at ROOT
        return false
    else 
        return PARENT.ISDESCENDANT(TREE)
end function
```

##### Is Sibling?
For this function, we are asking: is this node a sibling of the current instance? To determine this, we can get the parent of the current instance and then get the parents children. Finally, we check if the node in question is in that set of children.

```tex
function ISSIBLING(TREE)
    if TREE in PARENT's CHILDREN
        return true
    else 
        return false
end function
```

---

### Lowest common ancestor
In any tree, we can say that the root is a common ancestor to all of the nodes. We would like to get more information about the common ancestry of two nodes. For this function, we are asking: which node is the first place where this instance and the input node's ancestries meet? Similar to our ISDESCENDANT, we will work our way up the tree to find the point where they meet

- Base case: we are at our tree so return the tree OR we are at an ancestor of our tree so return the instance OR we are at the root so return nothing
- Recursive case: run the method from the parent.

```tex
function LOWESTANCESTOR(TREE)
    if at TREE
        return TREE
    else if ISANCESTOR(TREE)
        return instance
    else if at ROOT
        return NONE
    else
        return PARENT.LOWESTANCESTOR(TREE)
end function
```


---

### Path from the root
This function will generate the path which goes from the root to the current instance.
```tex
function PATHFROMROOT(PATH)
    if NOT ROOT
        PARENT.PATHFROMROOT(PATH)
    append ITEM to PATH
end function
```
