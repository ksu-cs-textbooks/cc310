---
title: "Doubly Linked Lists - Removal and Peek"
weight: 55
pre: "11. "
---
The process of removing a node from a doubly linked list is really no more difficult than from a singly linked list. The only difference is that instead of changing just one pointer, we now also need to modify the `previous` pointer in the node following the node we want to remove. For instance, if we want to remove node "3" from the following list,
 
![Doubly Linked List Detail](/images/9/9.10.double.png)
 
we simply modify the `next` pointer in node "-2" to point to node "23". Then, we modify the `previous` pointer in node "23" to point to node "-2". We then return the data in that node to the requesting function. 

![Doubly Linked List Remove](/images/9/9.12.remove.png)
 
## Removing at the Beginning

The `remove` operation removes the first node in the list. First, we check to ensure that there is at least one node in the list in line 1 and raise an exception if there is not. Now, the process is simple. We simply create a temporary pointer `temp` that points to the node we are going to delete in line 3 and then point `head` to `head.next`, which is the second node in the list. Then, in line 5, we check to see if the list is empty (`head == null`) and set `tail` to `null` if it is (it was pointing at the node we just removed). If the list is not empty, we do not need to worry about updating `tail`; however, we do need to set the `previous` pointer of the first node in the list to `null` (it was also pointing at the node we just removed). Finally, we decrement `size` in line 8 and then return the data in the node we just removed in line 9. Obviously, the operation runs in constant time since there are no loops.

```tex
function remove() returns data
	if size == 0	            (1)
		raise exception	        (2)
	end if
	temp = head		            (3)
	head = head.next	        (4)
	if head == null	            (5)
		tail = null	            (6)
	else
		head.previous = null	(7)
	end if
	size = size – 1	            (8)
	return temp.data	        (9)
end function
```

## Removing in the Middle

Removing a node at a specific index is very similar to the way we did it in singly linked lists. First, if we have an invalid `index` number, we raise an exception in line 2. Otherwise we check for the special cases of removing the first or last node in the list and calling the appropriate operations in lines 3 – 6. 
If we have no special conditions, we create a temporary pointer `curr` and then walk through our list in lines 7 – 9. Once we reach the node we want to remove, we simply update the next node's `previous` pointer (line 10) and the previous node's `next` pointer (line 11) and we have effectively removed the node from the list. We then decrement size in line 12 and return the `data` from the removed node in line 13. 

Since the operation relies on a loop to walk through the list, the operation runs in order $N$ time.

```tex
function removeAt(index) returns data
	if index < 0 OR index > size – 1	    (1)
		raise exception	                    (2)
	else if (index == 0)	                (3)
		return remove()	                    (4)
	else if index == size – 1	            (5)
		return removeLast()	                (6)
	else	
		curr = head.next;	                (7)
        for i = 1 to index -1 	            (8)
            curr = curr.next	            (9)
        end for

        curr.next.previous = curr.previous	(10)
        curr.previous.next = curr.next	    (11)
        size = size – 1	                    (12)
        return curr.data	                (13)
    end if
end function
```

## Removing at the End

Since we have added the `tail` pointer to the doubly linked list class, we can make removing a node at the end of the list run in constant time instead of running in order $N$ time. In fact, if you look at the code below for the `removeLast` operation, it is almost exactly the same as the constant time `removeFirst` operation. The only difference is that we have replaced the `head` pointer with the `tail` pointer and `head.next` with `tail.previous` in lines 3 – 7.

```tex
function removeLast() returns data
	if size == 0	        (1)
		raise exception	    (2)
	end if	
	temp = tail		        (3)
	tail = tail.previous	(4)
	if tail == null	        (5)
		head = null	        (6)
	else	
		tail.next = null	(7)
	end if
	size = size – 1	        (8)
	return temp.data	    (9)
end function
```

## PeekEnd

Another operation impacted by the addition of the `tail` pointer is the `peekEnd` operation. Since we can access the last node in the list directly, we just need to make sure that the list is not empty, which we do in lines 1 and 2. Then, we can return the `tail.data`.

```tex
function peekEnd() returns data
	if isEmpty()	        (1)
		raise exception 	(2)
	else	
		return tail.data	(3)
	end if
end function
```
