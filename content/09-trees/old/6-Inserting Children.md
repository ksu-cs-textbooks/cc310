---
title: "Inserting Children"
weight: 30
pre: "6. "
---

{{< youtube qFalue24DdE  >}}

When inserting children to a binary tree, we must take some special considerations. All of the node items in the left tree must be less than the parent node item and all of the node items in the right tree must be greater than the parent node item.

The general procedure for adding a child is the following: 
![Binary Tree Flowchart](images/14/4Binary_AddFlowChart.png)


Suppose that we have the following tree and we want to add a node with item '85'. Click the binary tree to see the resulting tree.

{{% expand title="![Tree To Add To](images/14/4Binary_Add.png)" %}} ![Tree Adding](images/14/4Binary_AddChild.gif) {{% /expand %}}


``` tex

function INSERT(VALUE)
    if node is empty:
        set nodes item to value
    else:
        if node.ITEM is VALUE
            return false
        else if node.ITEM > VALUE 
            LC = node`s left child
            if LC is NONE
                CHILD = new BINARYTREE with root.ITEM equal VALUE
                add CHILD to nodes children
                set node.LEFTCHILD equal to CHILD
                return true
            else
                return LC.INSERT(VALUE)
        else
            RC = node`s right child
            if RC is NONE
                CHILD = new BINARYTREE with root.ITEM equal VALUE
                add CHILD to nodes children
                set node.RIGHTCHILD equal to CHILD
                return true
            else
                return RC.INSERT(VALUE)
end function

```
