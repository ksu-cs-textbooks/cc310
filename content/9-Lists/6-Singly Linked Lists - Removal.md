---
title: "Singly Linked Lists - Removal"
weight: 30
pre: "6. "
---
The process of removing a node from a linked list is fairly straightforward. First, we find the node we want to remove from the list and then change the `next` pointer from the previous node in the list to the next node in the list.  This effectively bypasses the node we want to remove. For instance, if we want to remove node "3" from the following list,

![Linked List Remove 1](../../images/9/9.6.remove1.png)
 
we simply change the `next` pointer in the "-2" node to point to node "18" instead of node "3". Since no other nodes are pointing at node "3" it is effectively removed from our list as shown below. We then return the data in that node to the requesting function. Eventually, the garbage collector will come along and realize that nothing is referencing node "3" and put it back into available memory.

{{% notice info %}}

# Garbage Collector

Many programming languages, including Java and Python, automatically manage memory for us. So, as we create or delete objects in memory, a special subroutine called the _garbage collector_ will find and remove any objects that we are no longer using. This will help free up memory so we can use it again. 

Other languages, such as C, require us to do that manually. So, whenever we stop using objects, we would have to also remember to free the memory used by that object. Thankfully, we don't have to worry about that in this course!

{{% / notice %}}
 
## Removing at the Beginning

Removing an item at the beginning of a list is extremely simple. After checking our precondition in line 1, which ensures that the list is not empty, we create a temporary copy of the data in the first node in line 3 so we can return it later in line 6. However, the actual removal of the first node simply requires us to point `head` to the second node in the list (line 4), which is found at `head.next`. This effectively skips over the first node in the list. Finally, we decrement our `size` variable in line 5 to keep it consistent with the number of nodes now in the list. Since there are no loops, `removeFirst` runs in constant time.

```tex
function removeFirst() returns data
		if size == 0			(1)
			raise exception	    (2)
		end if
		temp = head.data		(3)
	head = head.next 	        (4)
	size = size – 1		        (5)
	return temp			        (6)
end function
```

## Removing in the Middle

Removing a node at a specific index in the list is more difficult than simply removing the first node in the list since we have to walk through the list to find the node we want to remove before we can actually remove it. In addition, while walking through the list, we must keep track of the current node as well as the previous node, since removing a node requires us to change the previous node in the list.

In our `removeAt` operation below, we first check our precondition in line 1 to ensure that the `index` provided is a valid index in the list. If it is, we check to see if `index` is 0 in line 3 and call the `removeFirst` operation in line 4 if it is. 

```tex
function removeAt(index) returns data
    if index < 0 OR index > size – 1	(1)
        raise exception	                (2)
    else if index == 0	                (3)
        return removeFirst()            (4)
    else
        curr = head.next	            (5)
        prev = head		                (6)

        for i = 1 to index - 1 	        (7)
            prev = curr	                (8)
            curr = curr.next	        (9)
        end for
        prev.next = curr.next	        (10)
        size = size – 1	                (11)
        return curr.data	            (12)
    end if
end function
```

Before we start our walk through the list using the `for` loop in lines 7 - 9, we declare two variables in lines 5 and 6:

* `curr` points to the current node in our walk, and
* `prev` points to the node before `curr` in the list.

Lines 7 – 9 are the `for` loop that we use to walk through the list to find the node at `index`. We simply update the values of `prev` and `curr` each time through the loop to point to the next node in the list.

Once we complete the `for` loop, `curr` is pointing at the node we want to remove and `prev` points at the previous node. Thus, we simply set `prev.next = curr.next` to bypass the `curr` node, decrement our size attribute by 1 to retain consistency, and return the data associated with the `curr` node.

Like the `insertAt` operation, the `removeAt` operation uses a loop and thus runs in order $N$ time.

## Removing Instances of a Node

If we want to remove all occurrences of a specific node from the list, we take the data we want to remove from the list and then search all nodes in the list, removing any whose data matches the data from the input node. We will return the number of nodes removed from the list.

```tex
function removeData(data)
	curr = head			            (1)
	index = 0				        (2)
	while (curr != null) 	        (3)
		if (curr.data == data) 	    (4)
			removeAt(index)	        (5)
		end if
		index = index + 1	        (6)
		curr = curr.next	        (7)
	end while	
end function
```

To simplify this operation, we will call the `removeAt` operation to actually remove the node from the list, leaving this operation to simply find the nodes whose data match the input `data`.  We will use two variables in this operation:

* `curr` will point to the current node we are checking, and
* `index` will keep track of the index of the `curr` node so we can use the `removeAt` operation.

The main part of the operation is a `while` loop (lines 3 – 7) that walks through the list, node by node. For each node in the list, we check if its data matches the input `data` in line 5, and then call `removeAt` to remove it from the list if it does. Then, each time through the loop, we increment `index` in line 7 and then point `curr` to the next node in the list in line 8. When our loop exits, we have removed all the nodes whose data matched the input `data`.

Since we walk through the entire list, the `removeData` operation runs in order $N$ time.
