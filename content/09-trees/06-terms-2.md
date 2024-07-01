---
title: "Terms II"
weight: 30
pre: "6. "
---

{{< youtube 86uWWXaanCo  >}}

We can describe the sizes of trees and position of nodes using different terminology, like level, depth, and height. 

![Family Tree](images/14/3Tree_FamilyTree.png)

- `Level` - The level of a node characterizes the distance between the node and the root. The root of the tree is considered level 1. As you move away from the tree, the level increases by one. 
    - For our family tree example, what nodes are in the following levels? Think about the answer and then click corresponding arrow. 
        {{% expand title="Level 1:" %}}<u>Myra</u> - Level 1 is always the root{{% /expand %}}
        {{% expand title="Level 2:" %}}<u>Raju, Joe, Zia</u> - These are the nodes which are 1 edge away from the root.{{% /expand %}}
        {{% expand title="Level 3:" %}}<u>Uzzi, Bert, Uma</u> - These are the nodes which are 2 edges away from the root. {{% /expand %}}
        {{% expand title="Level 4:" %}}<u>Bev, Ava, Ang</u> - These are the nodes which are 3 edges away from the root. {{% /expand %}}
        {{% expand title="Level 5:" %}}<u>Isla</u> - This is the only node which is 4 edges away from the root. {{% /expand %}}
        {{% expand title="Level 6:" %}}<u>Eoin</u> - This is the only node which is 5 edges away from the root. {{% /expand %}}
- `Depth` - The depth of a node is its distance to the root. Thus, the root has depth zero. `Level` and `depth` are related in that: `level = 1 + depth`.
    - For our family tree example, what nodes have the following depths? 
        {{% expand title="Depth 0:" %}}<u>Myra</u> - The root will always be at depth 0.{{% /expand %}}
        {{% expand title="Depth 1:" %}}<u>Raju, Joe, Zia</u> - These are the nodes which are 1 edge away from the root.{{% /expand %}}
        {{% expand title="Depth 2:" %}}<u>Uzzi, Bert, Uma</u> - These are the nodes which are 2 edge away from the root.{{% /expand %}}
        {{% expand title="Depth 3:" %}}<u>Bev, Ava, Ang</u> - These are the nodes which are 3 edge away from the root.{{% /expand %}}
        {{% expand title="Depth 4:" %}}<u>Isla</u> - This is the only node which is 4 edges away from the root.{{% /expand %}}
        {{% expand title="Depth 5:" %}}<u>Eoin</u> - This is the only node which is 5 edges away from the root.{{% /expand %}}
- `Height of a Node` - The height of a node is the **longest** path to a leaf descendant. The height of a leaf is zero.
    - For our family tree example, what nodes have the following heights?
        {{% expand title="Height 0:" %}}<u>Raju, Eoin, Ava, Bert, Ang</u> - The leaves always have height 0. {{% /expand %}}
        {{% expand title="Height 1:" %}}<u>Isla, Uma</u> - `Isla -> Eoin`  and `Uma -> Ang` {{% /expand %}}
        {{% expand title="Height 2:" %}}<u>Bev, Zia</u> - `Bev -> Isla -> Eoin` and `Zia -> Uma -> Ang` {{% /expand %}}
        {{% expand title="Height 3:" %}}<u>Uzzi</u> - `Uzzi -> Bev -> Isla -> Eoin`{{% /expand %}}
        {{% expand title="Height 4:" %}}<u>Joe</u> - `Joe -> Uzzi -> Bev -> Isla -> Eoin`{{% /expand %}}
        {{% expand title="Height 5:" %}}<u>Myra</u> - `Myra -> Joe -> Uzzi -> Bev -> Isla -> Eoin`{{% /expand %}}
- `Height of a Tree` - The height of a tree is equal to the height of the root. 
    - Our family tree would have height 5




