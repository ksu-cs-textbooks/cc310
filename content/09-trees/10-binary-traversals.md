---
title: "Binary Tree Traversals"
weight: 50
pre: "10. "
---

{{< youtube TNkWt307y84  >}}

In the first module we discussed two types of traversals: preorder and postorder. Within that discussion, we noted that for general trees, the preorder and postorder traversal may not be unique. This was due to the fact that children nodes are an unordered set.

{{% notice info %}}

We are now working with binary trees which have a defined child order. As a result, the preorder and postorder traversals will be **unique**! These means that for a binary tree when we do a preorder traversal there is exactly one string that is possible. The same applies for postorder traversals as well.

{{% / notice %}}


 Recall that these were defined as such: 
- Preorder Traversal (Remember: Root Children): 
    1. Access the root
    2. Run the preorder traversal on the children
- Postorder Traversal (Remember: Children Root): 
    1. Run the postorder traversal on the children
    2. Access the root. 

Now for binary trees, we can modify their definitions to be more explicit:
- Preorder Traversal (Remember: Root Left Right): 
    1. Access the root
    2. Run the preorder traversal on the left child
    3. Run the preorder traversal on the right child
- Postorder Traversal (Remember: Left Right Root): 
    1. Run the postorder traversal on the left child
    2. Run the postorder traversal on the right child
    3. Access the root. 
    
Let's practice traversals on the following binary tree. 

![Traversal Tree](images/14/4Binary_Traversal.png)

## Preorder Traversal

![Preorder](images/14/4Binary_Pre.gif)

## Postorder Traversal

![Postorder](images/14/4Binary_Post.gif)



    
