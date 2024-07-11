---
title: "Tree Algorithms"
weight: 30
pre: "6. "
---

We will now discuss the performance of the algorithms that we discussed in this course. When examining the performance of an algorithm we will look at the time and the space that it will require. 

- **Time**: To analyze the time of an algorithm, we will look at the number of operations required to complete the algorithm. 
- **Space**: To analyze the space requirement of an algorithm, we will look at the various variables within the algorithm. To calculate this, we can add up the space requirements for each variable within the algorithm


### Preorder and Postorder

```tex
function PREORDER(RESULT)
    append ITEM to RESULT
    FOR CHILD in CHILDREN
           CHILD.PREORDER(RESULT)
end function
```

```tex
function POSTORDER(RESULT)
   FOR CHILD in CHILDREN
           CHILD.POSTORDER(RESULT)
   append ITEM to RESULT
end function
```

- **Time**: The time required for preorder or postorder traversals will be linear with respect to the number of nodes. In a single iteration, we will execute the appending once and we will execute the for loop for each child. 
- **Space**: Since `RESULT` is a variable defined and stored outside of the algorithm, it does not factor into our space requirement. Then we must account for the variables `CHILD` and `CHILDREN`. In any given iteration, `CHILD` will be constant and `CHILDREN` will have size equal to the number of children for the node we are currently at. In total, this would give us a space requirement that is linear with respect to the number of nodes. 

### Inorder

```tex
function INORDER(RESULT)
    LEFTCHILD.INORDER(RESULT)
    append ITEM to RESULT
    RIGHTCHILD.INORDER(RESULT)
end function
```
- **Time**: For any given call to the inorder traversal, it will execute in constant time. We must factor in that we have a recursive function and as such, we will call the inorder traversal for each node. Thus our time requirement will be linear with respect to the number of nodes. 
- **Space**: Since `RESULT` is a variable defined and stored outside of the algorithm, it does not factor into our space requirement. Then we must account for the variable `ITEM`. This will have constant space and thus, the space requirement for the inorder traversal is constant. 
