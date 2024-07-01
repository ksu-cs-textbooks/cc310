---
title: "MyBinaryTree"
weight: 25
pre: "5. "
---
{{< youtube 0U5EXtcHcsU  >}}

Our implementation of binary trees will inherit from our MyTree implementation as binary trees are types of trees. Thus, MyBinaryTree will have the functionality of MyTree in addition to the following. 

![UML](images/14/binary_uml.png)

Attributes
---

The binary tree has two attributes
- Left Child: an instance of `MyBinaryTree`, the item should be less than the item of the parent.
- Right Child: an instance of `MyBinaryTree`, the item should be greater than the item of the parent.


Miscellaneous Functions
---

- Get Size
    - Will override the `MyTree` size function. If the tree is empty then we return zero. If the tree is not empty then call the `MyTree` size function. 

- Is Empty
    - Will return true if the node we have called the function from is empty and false if otherwise. 

- To Sorted List
    - Will get all of the nodes items and sort them
``` tex
function TOSORTEDLIST()
    LIST = []
    if there`s LEFTCHILD
        LIST = LIST + LEFTCHILD.TOSORTEDLIST
    LIST = LIST + ITEM
    if there`s RIGHTCHILD
        LIST = LIST + RIGHTCHILD.TOSORTEDLIST
    return LIST
```

