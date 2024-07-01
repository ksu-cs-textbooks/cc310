---
title: "Terms III"
weight: 35
pre: "7. "
---

{{< youtube Jurg4tZKCwI  >}}

When working with multidimensional data structures, we also need to consider how they would be stored in a linear manner. Remember, pieces of data in computers are linear sequences of binary digits. As a result, we need a standard way of storing trees as a linear structure. 

![Traversal Tree](images/14/3Tree_Traversal.png)

- `Path` - a path is a sequence of nodes and edges, which connect a node with its descendant. We can look at some paths in the tree above: 
    - From `Q` to `O`: `QRO`
    {{% expand title="From `Q` to `Y`:" %}}`QWY`{{% /expand %}}
    {{% expand title="From `R` to `P`:" %}}`RP`{{% /expand %}}

- `Traversal` is a general term we use to describe going through a tree. The following traversals are defined recursively. 

## Preorder Traversal

1. Access the root, record its value.
1. Run the preorder traversal each of the children

{{< youtube JthdRshLJP0  >}}


- The `Pre` refers to the root, meaning the root goes before the children.
- Remember: Root Children 
- For the above tree, the preorder traversal could result in: `QWYUERIOPTA`
![Preorder Traversal](images/14/3Tree_Preorder.gif)
       
       
## Postorder Traversal

1. Run the postorder traversal on each of the children
1. Access the root, record its value

{{< youtube eEZmsK-loUU  >}}


- The `Post` refers to the root, meaning the root goes after the children.
- Remember: Children Root 
- For the above tree, the postorder traversal could result in: `YUWEIOPRATQ`
![Postorder Traversal](images/14/3Tree_Postorder.gif)
        
---

When we talk about traversals for general trees we have used the phrase 'the traversal *could* result in'. We would like to expand on why 'could' is used here. Each of these general trees are the same but their traversals could be different. The key concept in this is that for a general tree, the children are an unordered set of nodes; they do not have a defined or fixed order. The relationships that are fixed are the parent/child relationships.
![Traversal Tree](images/14/3Tree_Traversal.png)
![Traversal Tree1](images/14/3Tree_Traversal1.png)
![Traversal Tree2](images/14/3Tree_Traversal2.png)

| Tree | Preorder | Postorder |
| --- | --- | --- |
| Tree 1 |`QWYUERIOPTA`|`YUWEIOPRATQ`|
| Tree 2 | `QETARIOPWUY` | `EATIOPRUYWQ` |
| Tree 3 | `QROPITAEWUY` | `OPIRATEUYWQ` |
