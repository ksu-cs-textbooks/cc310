---
title: "Tree Operations"
weight: 20
pre: "4. "
---

{{< youtube y02_6lWMVnQ  >}}

[Video Materials](video)

Along with understanding how trees work, we want to also be able to implement a tree of our own. We will now outline key components of a tree class. 

---

### MyTree

Recall that trees are defined recursively so we can build them from the leaves up where each leaf is a tree itself. Each tree will have three properties: the item it contains as an object, its parent node of type MyTree, and its children as a list of MyTrees. Upon instantiation of a new MyTree, we will set the item value and initialize the parent node to None and the children to an empty list of type MyTree. 

![UML](/images/14/tree_uml.png)

Suppose that we wanted to construct the following tree.

![Tree](/images/14/2Tree_Implementation.png)

We would start by initializing each node as a tree with no parent, no children, and the item in this instance would be the characters. Then we build it up level by level by add the appropriate children to the respective parent.

{{% notice info %}}

**Disclaimer:** This implementation will not prevent all cycles. In the next module, we will introduce steps to prevent cycles and maintain true tree structures.

{{% / notice %}}

---

### Finding a child

In this method, we will take a value as input and then check if that value is the item of a child of the current node. If the value is not the item for any of the node's children then we should return none.  

```tex
function FINDCHILD(VALUE)
    FOR CHILD in CHILDREN
        IF CHILD's ITEM is VALUE
            return  CHILD
    return NONE
end function
```

---

### Getting  children, item, parent, or degree

Each of these will be rather straight forward; children, item, and parent are all attributes of our node, so we can have a getter function that returns the respective values. The slightly more involved task will be getting the degree. Recall that the degree of a node is equal to the number of children. Thus, we can simply count the number of children and return this number for the degree. 

---

### Checking node type

We will have two functions to check the node type: one to determine if the node is a leaf and one to determine if it is a root. The definition of a leaf is a node that has no children. Thus, to check if a node is a leaf, we can simply check if the number of children is equal to zero. Similarly, since the definition of a root is a node with no parent, we can check that the parent attribute of the node is None. 

---

### Adding a child 

{{< youtube T5gy1Q7hx1w  >}}

When we wish to add a child, we must fisrt make sure we are able to add the child. 

1. Check that the child is an instance of `MyTree`
1. Make sure the child doesn't already have a parent
1. Make sure the child isn't already a child of the parent 

We will return true if the child was successfully added and false otherwise while raising the appropriate errors. 

```tex
function ADDCHILD(CHILD)
    IF CHILD has PARENT
        throw exception
    IF CHILD is CHILD of PARENT
        return FALSE
    ELSE
        append CHILD to PARENT's children
        set CHILD's parent to PARENT
        return TRUE
end function
```

As an example, lets walk through the process of building the tree above: 

1. Instantiate MyTree `a` with item 'A'
1. Instantiate MyTree `b` with item 'B'
1. Instantiate MyTree `c` with item 'C'
1. Instantiate MyTree `d` with item 'D'
1. Instantiate MyTree `e` with item 'E'
1. Instantiate MyTree `f` with item 'F'
1. Instantiate MyTree `g` with item 'G'
1. Instantiate MyTree `h` with item 'H'
1. Instantiate MyTree `i` with item 'I'
1. Add child tree `g` to tree `d`
1. Add child tree `h` to tree `d`
1. Add child tree `i` to tree `d`
1. Add child tree `e` to tree `b`
1. Add child tree `f` to tree `b`

Once we have completed that, visually, we would have the tree above and in code we would have: 

- MyTree `a` with parent_node = None, item = 'A', children = {`b`,`c`,`d`}
- MyTree `b` with parent_node = `a`, item = 'B', children = {`e`,`f`}
- MyTree `c` with parent_node = `a`, item = 'C', children = \{ \}
- MyTree `d` with parent_node = `a`, item = 'D', children = {`g`,`h`,`i`}
- MyTree `e` with parent_node = `b`, item = 'E', children = \{ \}
- MyTree `f` with parent_node = `b`, item = 'F', children = \{ \}
- MyTree `g` with parent_node = `d`, item = 'G', children = \{ \}
- MyTree `h` with parent_node = `d`, item = 'H', children = \{ \}
- MyTree `i` with parent_node = `d`, item = 'I', children = \{ \}

**Note:** When adding a child we must currently be at the node we want to be the parent. Much like when you want to add a file to a folder, you must specify exactly where you want it. If you don't, this could result in a wayward child.

---

### Removing a child

{{< youtube QtfZIUMPrJY  >}}

In the case of removing a child, we first need to check that the child we are attempting to remove is an instance of `MyTree`. We will return true if we successfully remove the child and false otherwise. 

```tex
function REMOVECHILD(CHILD)
    IF CHILD in PARENT'S children
        REMOVE CHILD from PARENT's children
        SET CHILD's PARENT to NONE
        return TRUE
    ELSE
        return FALSE
end function
```

As with adding a child, we need to ensure that we are in the 'right place' when attempting to remove a child. When removing a child, we are not 'erasing' it, we are just cutting the tie from parent to child and child to parent. Consider removing `d` from `a`. Visually, we would have two disjoint trees, shown below:

![Tree 2](/images/14/2Tree_Implementation2.png)

In code, we would have: 

- MyTree `a` with parent_node = None, item = 'A', children = {`b`,`c`}
- MyTree `b` with parent_node = `a`, item = 'B', children = {`e`,`f`}
- MyTree `c` with parent_node = `a`, item = 'C', children = \{ \}
- MyTree `d` with parent_node = None, item = 'D', children = {`g`,`h`,`i`}
- MyTree `e` with parent_node = `b`, item = 'E', children = \{ \}
- MyTree `f` with parent_node = `b`, item = 'F', children = \{ \}
- MyTree `g` with parent_node = `d`, item = 'G', children = \{ \}
- MyTree `h` with parent_node = `d`, item = 'H', children = \{ \}
- MyTree `i` with parent_node = `d`, item = 'I', children = \{ \}



