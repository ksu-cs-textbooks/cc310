---
title: "Summary"
weight: 65
pre: "13. "
---

In this module we have introduce vocabulary related to trees and what makes a tree a tree. To recap, we have introduced the following:

- `Child` - a node with an edge that connects to another node closer to the root.
- `Degree`
    - `Degree of a node` - the number of children a node has. The degree of a leaf is zero. 
    - `Degree of a tree` - the number of children the root of the tree has.
- `Edge` - connection between two nodes. In a tree, the edge will be pointing in a downward direction. 
- `Leaf` - a node with no children.
- `Node` - the general term for a structure which contains an item, such as a character or even another data structure. 
- `Parent` - a node with an edge that connects to another node further from the root. We can also define the root of a tree with respect to this definition; 
- `Root` - the topmost node of the tree; a node with no parent.

Now we will work on creating our own implementation of a tree. These definitions will serve as a resource to us when we need refreshing on meanings; feel free to refer back to them as needed.

We discussed more terminology related to trees as well as tree traversals. To recap the new vocabulary: 

- `Ancestor` - The ancestors of a node are those reached from child to parent relationships. We can think of this as our parents and the parents of our parents, and so on. 
- `Depth` - The depth of a node is its distance to the root. Thus, the root has depth zero. `Level` and `depth` are related in that: `level = 1 + depth`.
- `Descendant` - The descendants of a node are those reached from parent to child relationships. We can think of this as our children and our children's children and so on. 
- `Height of a Node` - The height of a node is the **longest** path to a leaf descendant. The height of a leaf is zero.
- `Height of a Tree` - The height of a tree is equal to the height of the root. 
- `Level` - The level of a node characterizes the distance the node is from the root. The root of the tree is considered level 1. As you move away from the tree, the level increases by one. 
- `Path` - a sequence of nodes and edges which connect a node with its descendant.
- `Siblings` - Nodes which share the same parent 
- `Traversal` is a general term we use to describe going through a tree. The following traversals are defined recursively. 
    - Preorder Traversal (Remember: Root Children or Root Left Right): 
        1. Access the root
        2. Run the preorder traversal on the children
    - Postorder Traversal (Remember: Children Root or Left Right Root): 
        1. Run the postorder traversal on the children
        2. Access the root. 
    - Inorder Traversal on Binary Trees (Remember: Left Root Right)