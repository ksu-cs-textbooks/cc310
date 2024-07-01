---
title: "MyTree Recursive III"
weight: 40
pre: "8. "
---
### Traversals
In this module we have talked about two traversals: preorder and postorder. Both of these are defined recursively and the prefix refers to the order of the root.

##### Preorder
In a preorder traversal, first we access the root and then run the preorder traversal on the children. 

```tex
function PREORDER(RESULT)
    append ITEM to RESULT
    FOR CHILD in CHILDREN
           CHILD.PREORDER(RESULT)
end function
```

##### Postorder 
In a postorder traversal, first we run the postorder traversal on the children then we access the root. 

```tex
function POSTORDER(RESULT)
   FOR CHILD in CHILDREN
           CHILD.POSTORDER(RESULT)
   append ITEM to RESULT
end function
```
