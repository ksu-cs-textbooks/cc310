---
title: "Removing Children"
weight: 35
pre: "7. "
---
{{< youtube uyhC6GcyBW4  >}}

Removing children is not as straightforward as inserting them. The general procedure for removing a child is to replace that nodes value with its smallest right descendant. First we will traverse the binary tree until we find the node with the value we are trying to remove (lines 18-32 below). Then we have three separate cases, discussed in detail below.

Removing a Leaf
---
Removing a leaf is the most straightforward. We remove the value from the node and then sever the connection between parent and child. (lines 5-7 below)

Suppose we have this binary tree and we want to remove value `5`. What do you think the resulting binary tree will look like? Click the binary tree to see the result.

{{% expand title="![Tree to Remove Leaf](images/14/4Bin_Remove.png)" %}} ![Result of Remove Leaf](images/14/4Bin_Remove2.png) {{% /expand %}}


Removing a Node without Right Child
---
When we remove a value from a node that does not have a right child, we cannot replace the value with the smallest right child. In this instance we will instead replace the value with the smallest left child then prune the tree to clean it up. Once we replace the value, we must switch the node's left child to be the right child in order to maintain proper binary tree structure. (lines 8-13 below)

Suppose we have this binary tree and we want to remove value `4`. What do you think the resulting binary tree will look like? Click the binary tree to see the result.

{{% expand title="![Tree to Remove w/o RightChild](images/14/4Bin_Remove2.png)" %}} ![Result of Remove w/o RightChild](images/14/4Bin_Remove3.png) {{% /expand %}}

Removing a Node with Right Child
---
When we remove a value from a node that has a right child, we can replace the value with the nodes smallest right child. (Lines 14-17 Below)


Suppose we have this binary tree and we want to remove value `10`. What do you think the resulting binary tree will look like? Click the binary tree to see the result.

{{% expand title="![Tree to Remove with RightChild](images/14/4Bin_Remove.png)" %}} ![Result of Remove with RightChild](images/14/4Bin_Remove1.png) {{% /expand %}}


Complete Pseudocode
---


``` tex 
1. function REMOVE(VALUE)
2.    if node is empty:
3.        error
4.    if node.ITEM is VALUE
5.        if node is a leaf
6.            set node.ITEM to none
7.            return TRUE
8.        else if node has no right child
9.            node.ITEM = LEFTCHILD.REMOVESMALLEST()
10.           prune left-side
11.           store left child in right child
12.           set left child to none    
13.           return TRUE
14.        else
15.            node.ITEM = RIGHTCHILD.REMOVESMALLEST()
16.            prune right-side
17.            return TRUE
18.    else
19.        if node.ITEM > VALUE
20.            if node has LEFTCHILD
21.                SUCCESS = LEFTCHILD.REMOVE(VALUE)
22.                prune left-side
23.                return SUCCESS
24.            else
25.                return FALSE
26.        else
27.            if node has RIGHTCHILD
28.                SUCCESS = RIGHTCHILD.REMOVE(VALUE)
29.                prune right-side
30.                return SUCCESS
31.            else
32.                return FALSE
33. end function
```

Extras for Removal
---
We use the pruning functions to severe the tie between parent and child nodes.
``` tex
function PRUNERIGHT()
    if RIGHTCHILD has no value
        REMOVECHILD(RIGHTCHILD)
        set this nodes RIGHTCHILD former RIGHTCHILDs RIGHTCHILD
        if RIGHTCHLID is not none
            ADDCHILD(RIGHTCHILD)
end function
```

``` tex
function PRUNELEFT()
    if LEFTCHILD has no value
        REMOVECHILD(LEFTCHILD)
        set this nodes LEFTCHILD former LEFTCHILDs RIGHTCHILD
        if LEFTCHILD is not none
            ADDCHILD(LEFTCHILD)
end function
```

We use the remove smallest function to retrieve the smallest value in the binary tree which will replace our value.
``` tex
function REMOVESMALLEST()
    if node has left child
        REPLACEMENT = LEFTCHILD.REMOVESMALLEST
        prune left-side
        return REPLACEMENT
    else
        REPLACEMENT = node.ITEM
        if node has right child
            node.ITEM = RIGHTCHILD.REMOVESMALLEST()
            prune right-side
        else
            node.ITEM = NONE
        return REPLACEMENT
end function
```



