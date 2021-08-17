---
title: "List-Based Stacks"
weight: 40
pre: "8. "
---
{{% youtube Chs-MJlCbdg %}}

If we implement a stack using a singly linked list, we can simplify many things about the implementation. First of all, we can totally remove the `isFull`, `doubleCapacity`, and `halveCapacity` operations since we can grow and shrink our list-based stack as needed. The rest of the operations can be implemented directly with list operations. The front of the list will be the top of the stack since the operations to insert and remove items from the front of list are very efficient.

To implement our stack, we assume we have declared a linked list object named `list`.

## Push

As expected, the `push` operation is almost trivial. We simply call the list `prepend` operation to insert the data into the front of the list.

```tex
function push(data)
	list.prepend(data)
end function
```

## Pop

Like `push`, the `pop` operation is also easily implemented using the `removeFirst` operation of our linked list. As long as the list is not empty, we simply return the data from the first item when we remove it from the list.

```tex
function pop() returns data
	if list.isEmpty() then
		throw exception
	end if
    return list.removeFirst().data
end function
```

## isEmpty
The `isEmpty` operation is even easier. It is implemented by simply returning the results of the list `isEmpty` operation.

```tex
function isEmpty() return boolean
	return list.isEmpty()
end function
```

## Peek
The stack `peek` operation is also straightforward. To implement the `peek` operation we simply return the results from the list `peek` operation, which returns the `data` from the first node in the list.

```tex
function peek() returns data
    return list.peek()
end function
```

As we can see, each of the major operations for a stack is implemented easily using list operations that run in constant time. This makes list-based stacks extremely efficient data structures to use.
