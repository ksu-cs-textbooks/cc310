---
title: "List Iterators"
weight: 85
pre: "17. "
---

{{% notice note %}}

You will not be asked to implement a list iterator, but it is an interesting concept to study. Most languages that have a `foreach` loop construct use iterators behind the scenes to keep track of the current position in the list. This is also why you should not modify the structure of the list while iterating through it using a `foreach` loop. 

{{% /notice %}}

{{< youtube iHeF6fzVIL8  >}}

An iterator is a set of operations a data structure provides to allow users to access the items in the data structure sequentially, without requiring them to know its underlying representation. There are many reasons users might want to access the data in a list. For instance, users may want to make a copy of their list or count the number of times a piece of data was stored in the list. Or, the user might want to delete all data from a list that matches a certain specification. All of these can be handled by the user using an iterator. 

At a minimum, iterators have two operations: `reset` and `getNext`. Both of these operations use the list class's `current` attribute to keep track of the iterator's current node.

## Reset

The `reset` operation initializes or reinitializes the `current` pointer. It is typically used to ensure that the iterator starts at the beginning of the list. All that is required is for the `current` attribute be set to `null`.

```tex
function reset()
  current = null
end function
```

## Get Next

The main operation of the iterator is the `getNext` operation. Basically, the `getNext` operation returns the next available node in the list if one is available.  It returns `null` if the list is empty or if `current` is pointing at the last node in the list.

Lines 2 and 3 in the `getNext` operation check to see if we have an empty list, which results in returning the `null` value. If we have something in the list but `current` is `null`, this indicates that the `reset` operation has just been executed and we should return the data in the first node. Therefore, we set `current = head` in line 6.  Otherwise, we set the `current` pointer to point to the next node in the list in line 8. 

{{< highlight lineNos="true" lineNoStart="1" type="py" >}}
function getNext() returns data
  if isEmpty()
    return null
  end if 
  if current == null
    current = head
  else
    current = current.next
  end if
  if current == null
    return null
  else
    return current.data
  end if
end function
{{< /highlight >}}

Next we return the appropriate data. If `current == null` we are at the end of the list and so we return the `null` value in line 11. If `current` is not equal to `null`, then it is pointing at a node in the list, so we simply return `current.data` in line 13.

## Remove current

While not technically part of the basic iterator interface, the `removeCurrent` operation is an example of operations that can be provided to work hand-in-hand with a list iterator. The `removeCurrent` operation allows the user to utilize the iterator operations to find a specific piece of data in the list and then remove that data from the list. Other operations that might be provided include being able to replace the data in the current node, or even insert a new piece of data before or after the current node.

The `removeCurrent` operation starts by checking to make sure that `current` is really pointing at a node. If it is not, then the condition is caught in line 2 and an exception is raised in line 3. Next, we set the `next` pointer in the previous node to point to the current node's `next` pointer in lines 5 - 9, taking into account whether the current node is the first node in the list. After that, we set the next node's `previous` pointer to point back at the previous node in line 10 - 14, considering whether the node is the last node in the list. Finally, we decrement `size` in line 15.

```tex
function removeCurrent()
  if current == null
    raise exception
  end if
  if current.previous != null
    current.previous.next = current.next
  else
    head = current.next
  end
  if current.next != null
    current.next.previous = current.previous
  else
    tail = current.previous
  end if
    current = current.previous
  size – size – 1
end function
```

## Using an Iterator

There are several applications for list iterators. For our example, we will use the case where we need a function to delete all instances of data in the list that match a given piece of data. Our `deleteAll` function resides outside the `list` class, so we will have to pass in the `list` we want to delete the `data` from. 
We start the operation by initializing the list iterator in line 2, followed by getting the first piece of data in the list in line 3. Next, we'll enter a `while` loop and stay in that loop as long as our copy of the current node in the list, `listData`, is not `null`. When it becomes `null`, we are at the end of the list and we can exit the loop and the function.

```tex
function deleteAll(list, data)
  list.reset()
  listData = list.getNext()
  while listData != null
    if listData == data
      list.removeCurrent()
    end if	
    listData = list.getNext()
  end while
end function
```

Once in the list, it's a matter of checking if our `listData` is equal to the `data` we are trying to match. If it is, we call the list's `removeCurrent` operation. Then, at the bottom of the list, we get the next piece of data from the list using the list iterator's `getNext` operation.

By using a list iterator and a limited set of operations on the current data in the list, we can allow list users to manipulate the list while ensuring that the integrity of the list remains intact. Since we do not know ahead of time how a list will be used in a given application, an iterator with associated operations can allow the user to use the list in application-specific ways without having to add new operations to the list data structure.
