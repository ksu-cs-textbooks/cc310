---
title: "Singly Linked Lists - Other Operations"
weight: 35
pre: "7. "
disableMathJax: false
---
## isEmpty

The list `isEmpty` operation is rather straightforward. We simply need to return the truth of whether `head.next` has a null pointer. Obviously, `isEmpty` runs in constant time.

```tex
function isEmpty() returns boolean
    return head == NULL       (1)
end function
```

## peek

The `peek` operation is designed to return the data from the last node inserted into the list, which is the node pointed at by `head`. This is easy to do; however, we must ensure that we check to see if the list is empty in line 1 before we return the `head.data` in line 3. Due to its simple structure, the run time of the `peek` operation is constant.

```tex
function peek() returns data
	if isEmpty()			(1)
		raise exception		(2)
	end if
	return head.data		(3)
end function
```

## peekEnd

The `peekEnd` operation is designed to return the first node inserted into the list, which is now the last node in the list. Like the `peek` operation, we must ensure the list is not empty in line 1 before actually searching for the end of the list. Lines 3 – 5 walk through the list using a `while` statement until `curr.next` is null, signifying that `curr` is pointing at the last node in the queue. Finally, line 6 simply returns the `data` in the last node. Since `peekEnd` must walk through the entire list to find the last node, it runs in order $N$ time.

```tex
function peekEnd() returns data
	if isEmpty()			    (1)
		raise exception		    (2)
	end if
    curr = head 			    (3)
    while curr.next != null		(4)
        curr = curr.next		(5)
    end while
    return curr.data			(6)
end function
```
