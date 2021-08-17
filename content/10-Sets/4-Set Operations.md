---
title: "Set Operations"
weight: 20
pre: "4. "
---
In this section, we will walk through the pseudocode for some basic set operations. We will build our set class using the doubly linked list class. In this way, we can build from the functionality that is already developed. So, in the set class, we will declare `mySet` as a doubly linked list and use that throughout our operations.

```tex
mySet = new doubleLinkedList()
```

## Contains

The first operation we will look at is the `contains` operation, which checks to see if a given object already exists in our set. This operation is generally very useful, which we will see in the operations below.

The pseudocode for the `contains` operation is shown below. We will use the list iterator built into our doubly linked list class to help us walk through the list searching for the object `o`. So, in line 1, we call the `reset` function and then the `getNext` operation in line 2 to get the first item in the `mySet` list. 


```tex
function contains(object o) returns Boolean
    mySet.reset()	            (1)
	obj = mySet.getNext()	    (2)
	while obj != null	        (3)
		if (obj == o)	        (4)
			return true	        (5)
		end if
		obj = mySet.getNext()	(6)
	end while
	return false	            (7)
end function
```

We then enter a `while` loop in line 3, where we will stay until either we find the object in our list, or we reach the end of the list. Once inside the loop, we check to see if the object from the list is equal to the object we are searching for in line 4. If it is, we return `true` in line 5 and we are done. If they are not equal, we get the next object from `mySet` and return to the top of the loop. If we reach the end of the list without finding our object, we will exit the loop and return `false` in line 7.

## Add

The `add` operation is relatively straightforward. The only thing we need to check is whether or not the object is already in `mySet`. In this case, instead of raising an exception when we try to add a duplicate object, we will return `true` if we add the object and `false` if we do not. This is because often, the user only really cares that the object is in the set after calling `add` and does not care if it was already there.

As shown, the pseudocode for the `add` operation is fairly straightforward. In lines 1 and 2, we call the `contains` operation to determine if the object already exists in `mySet` and return the value `false` if it does. Otherwise, we simply call the list operation `append` to insert the object into the list.

```tex
function add(object o) returns Boolean
	if (contains(o))	   (1)
		return false	   (2)
	else
        mySet.append(o)	   (3)
		return true	       (4)
	end if
end function
```

## Remove

The `remove` operation is very similar to the `contains` operation, except this time we want to remove the item if it exists in the set. We can use the `removeCurrent()` operation to remove the current item that our iterator is pointing to from the list. Again, like the `add` operation, we will return `false` if the operation does not actually remove an item from the list. Otherwise, the operation will return `true`.

```tex
function remove(object o) returns Boolean
    mySet.reset()	                (1)
	obj = mySet.getNext()	        (2)
	while obj != null	            (3)
		if (obj == o)	            (4)
            mySet.removeCurrent()	(5)
			return true	            (6)
		end if
		obj = mySet.getNext()	    (7)
	end while
	return false	                (8)
end function
```

## Intersection

The `intersection` operation creates a new set that has only elements that exist in both sets under consideration. In code, we basically accomplish this by looping through the elements in one set and then checking to see if they exist in the other set. If they do, then we include them in the intersection.

To follow that basic algorithm, the pseudocode below uses the list iterator operations to loop through and look at each element in `mySet`.  We will create a new set, `result,` to hold the intersection of `mySet` and `set2` in line 1. Then we get the first element from `mySet` by calling the list `reset` operation in line 2 and the `getNext` operation in line 3. 

```tex
function intersection(set2) returns set
	result = new set()	            (1)

    mySet.reset()	                (2)
	obj = mySet.getNext()	        (3)

	while obj != null	            (4)
		if (set2.contains(obj))	    (5)
			result.add(obj)	        (6)
        end if
		obj = mySet.getNext()	    (7)
	end while

	return result	                (8)
end function
```

Lines 4 – 7 implement the loop that walks through each element in `mySet`. If the current object is contained in `set2` (line 5), the operation calls the `add` operation to insert `obj` into the `result` set. Line 7 gets the next element from `mySet` and loops back to the top.

Eventually, we will look at each element in `mySet` and fall out of the loop. When that happens, the intersection operation is complete, and it returns the `result` set in line 8

## Union

The `union` operation is similar to the `intersection` operation in that we will need to use the list iterator operations to walk through our two sets. The difference lies in what we include in the new `result` set. While we only walked through `mySet` in the `intersection` operation, picking only those objects that existed in `set2`, here we will walk through both sets adding all their elements to the `result` set.

The code starts in line 1 by creating our `result` set. Then, lines 2 and 3 reset the `mySet` iterator and get the first item from `mySet`. Lines 4 – 6 form the `while` loop that we use to walk through the entire set of objects in `mySet`. This time, however, we simply add every element we find in line 5 before getting the next object in line 6.

```tex
function union(set2) returns set
	result = new set()	           (1)

    mySet.reset()	               (2)
	obj = mySet.getNext()	       (3)
    
	while obj != null	           (4)
		result.add(obj)	           (5)
		obj = mySet.getNext()	   (6)
	end while

    set2.reset()	               (7)
	obj = set2.getNext()	       (8)
    
	while obj != null	           (9)
		result.add(obj)	           (10)
		obj = set2.getNext()	   (11)
	end while

	return result	               (12)
end function
```

Lines 7 – 11 duplicate the loop function above, only using `set2` instead of `mySet`.  We don't have to worry about adding duplicate items in line 10, since as we saw above, our `add` operation will not allow duplicates to be added to the set. Finally, we return the `result` set, which holds the union of `mySet` and `set2`.

## isSubset 

Instead of using the `intersection` operation directly to compute the `isSubset` operation, we will compute the value of `isSubset` directly to make it more efficient. If we use `intersection` directly, we will end up looping through the members of one of the sets at least two times (once to compute the intersection and once to check equality). Computing `isSubset` directly only loops through one of the sets once.

The `isSubset` operation below is very much like the `intersection` operation as we have a loop in lines 3 - 6 that checks each element of `set2` and checks to see if it is in `mySet`. The difference between the two operations is that in the `isSubset` operation, we do not build a third `result` set. Instead, if any element in `set2` is not found in `mySet`, then we return `false` since not all elements of `set2` are contained in `mySet`. If we get all the way through the loop, we have checked that each element in `set2` was found in `mySet` and we can return `true`; `set2` is a subset of `mySet`.

```tex
function isSubset(set2) returns boolean
    set2.reset()	                (1)
	obj = set2.getNext()	        (2)

	while obj != null	            (3)
		if (! mySet.contains(obj))	(4)
			return false	        (5)
        end if
		obj = set2.getNext()	    (6)
	end while

	return true	                    (7)
end function
```
