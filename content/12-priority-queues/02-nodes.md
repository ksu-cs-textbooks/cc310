---
title: "Node Relationships"
weight: 10
pre: "2. "
---

{{< youtube TZZiihhBXco  >}}

Heaps can be viewed in two forms: as a tree or as an array. We will use the array style in code but we can have the tree structure in the back of our mind to help understand the order of the data. Here is an example of the heap as a tree on the left and the heap as an array on the right. 

![](images/17/Mod10_heap_and_array_numbered.svg)

The root of the heap will always be the first element. Then we can base the numbering of the following nodes from left to right and top to bottom. For example, the left child of the root will be the second entry and the right child will be the third.

### Accessing Indices

For full functionality of our heap, we want to be able to easily determine the parent of a node as well as the children of a node. 

{{% notice info "Critical Thinking" %}}

Using just the array, how can we determine the parent of a node? In the example above, how can we determine the parent of the node with value 18?

{{% / notice %}}


We can formulate the relationships between parent and children nodes mathematically. For a node at index `i`, we can say that the left child of `i` will be at index `2i` and the right child will be at `2i+1`. Similarly, we can say that the parent of node `i` will be at index `floor(i/2)`. 

{{% notice info %}}

The function `floor(x)` like in `floor(i/2)` will round decimal values down to the next whole number. Some examples:
- `floor(3.2)=3`
- `floor(1.9999)=1`
- `floor(4)=4` 

{{% / notice %}}

![](images/17/heap_numbering.svg)


| Node | Parent | Left Child | Right Child |
| --- | --- | --- | --- | 
| `i` | `floor(i/2)` | `2i` | `2i + 1` |
| 1 | N/A | `2*1=2` | `2*1+1=3`|
| 2 | `floor(2/2)=1` | `2*2=4` | `2*2+1=5` |
| 3 | `floor(3/2)=1` | `2*3=6` | `2*3+1=7` |
| 4 | `floor(4/2)=2` | `2*4=8` | `2*4+1=9` |
| 5 | `floor(5/2)=2` | `2*5=10` | `2*5+1=11` |

### Try It!

Consider the following example and try to work some out for yourself. 

![](images/17/Mod10_justarray.svg)

For example, if we ask for the parent of the node with value 27, our answer would be the node with value 35 The node with value 27 has index 5. Thus, the parent of that node will have index `floor(5/2)=2`. Node 35 is at index two, as such, node 35 is the parent of node 27.  

{{% expand title="Left child of the node with value 24:" %}}
The node with value three. Node 24 has index 4, so the left child will be at index 2*4=8. That corresponds to the node with value 3.
{{% /expand %}}

{{% expand title="Right child of the node with value 44:" %}}
The node with value twelve. Node 44 has index 3, so the right child will be at index (2*3)+1=7. That corresponds to the node with value 12.
{{% /expand %}}

{{% expand title="Parent of the node with value 36:" %}}
The node with value forty-four. Node 36 has index 6, so the parent will be at index floor(6/2)=3. That corresponds to the node with value 44.
{{% /expand %}}


{{% notice info %}}

In a heap where `n` is the size of heap, the elements `floor(n/2)+1` through `n` will always be leaves. If we assume that we have just the 12 elements in this example, then based on this formula, elements 7 through 12 must be leaves. We can verify this in the tree representation!

![](images/17/heap_numbering.svg)

{{% / notice %}}
