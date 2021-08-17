---
title: "Hash Table Based Sets"
weight: 30
pre: "6. "
---
{{% youtube j5TWEWJgJkk %}}

In this section, we walk through the pseudocode for some basic set operations built on our hash table class above. In this new version of the set class, we declare `mySet` as a hash table and use that throughout our operations.

```tex
mySet = new HashTable()
```

When using a hash table to implement sets, one of the most important choices we must make is what to use for a key. This is really difficult in the case of sets since we do not know exactly what types of objects may be put into the set. Our only real option at this point is just to use the entire object as our key. Our choice to use a default hash function in our hash table turns out to be a good one (at least in modern languages such as Python, Java, and C#), since most default hash functions work on any type of objects.

Next, we discuss the implementation of the important set operations using hash tables.

## Contains

The `contains` operation is straightforward since we are using the entire object as the key. We simply return the value from the hash table `containsKey` operation, which performs the exact function we need.

```tex
function contains(object o) returns boolean
    return mySet.containsKey(o)         (1)
end function
```

## Add

The `add` operation maps almost exactly to the hash table `put` operation except that the `put` operation does not return a boolean value. So, we first check to see if the key is already contained in the hash table. If so, we just return `false`, since we don't need to add the value to the set. Otherwise, we add a new tuple to the hash table, and then return `true`.

```tex
function add(object o) returns boolean
    if mySet.containsKey(o)
        return false
    end if
    mySet.put(o, o)
    return true
end function
```

## Remove

The set `remove` operation maps almost exactly to the hash table `remove` operation, so we just call it and then check to see if the result is not null. If it is null, we will return `false` since the element was not in the set; otherwise we return `true`.

```tex
function remove(object o) returns boolean
    return mySet.remove(o) != null
end function
```

## Intersection

The `intersection` operation creates a new set that has only elements which exist in both sets under consideration. In code, we basically accomplish this by looping through the elements in one set and then checking to see if they exist in the other set. If they do, then we include them in the intersection.

The pseudocode follows that basic algorithm using the hash table iterator to loop through and look at each element in `set1`.  We start by creating a new set, `result,` to hold the intersection of `set1` and `set2` in line 1. Then we get the first element pair from `set1` by calling the hash table `reset` operation in line 2 and the `getNext` operation in line 3. 

```tex
function intersection(set1, set2) returns set
    result = new Set()	                    (1)

    set1.reset()	                        (2)
    current = set1.getNext()	            (3)
    while current != null	                (4)
        if set2.contains(current.getKey())	(5)
            result.add(current.getKey())	(6)
        end if
        current = set1.getNext()	        (7)
    end while

    return result	                        (8)
end function
```

Lines 4 – 7 implement the loop that walks through each element in `set1`. If the current element is contained in `set2` (line 5), the operation calls the `add` operation to insert the key of the `current` element into the `result` set. Line 7 gets the next element from `set1` and loops back to the top.
Eventually, we look at each element in `set1` and fall out of the loop. When that happens, the intersection operation is complete, and it returns the `result` set in line 8.

## Union

The `union` operation is similar to the `intersection` operation in that we need to use the hash table iterator operations to walk through our sets. The difference lies in what we include in the new `result` set. While we only walked through `set1` in the `intersection` operation, picking only those objects that existed in `set2`, here we start by copying all elements from `set2` into the `result` set and then walk through `set1` adding each of its elements to the `result` set as well. (Here we don't need to worry about adding duplicates since the `add` operation takes care of that for us.)

The code starts in line 1 by making a `copy` of `set2` and assigning it to our new `result` set. Then, lines 2 and 3 reset the `set1` iterator and get the first item from `set1`. Lines 4 – 6 form the `while` loop that we use to walk through each element in `set1`. This time, however, we simply add every element we find in line 5 before getting the next object in line 6. Once the loop exists we are done and we return the `result` set in line 7.

```tex
function union(set1, set2) returns set
    result = set2.copy()	            (1)

    set1.reset()	                    (2)
    current = set1.getNext()	        (3)
    while current != null	            (4)
        result.add(current.getKey())	(5)
        current = set1.getNext()	    (6)
    end while

    return result	                    (7)
end function
```

## isSubset

The `isSubset` operation below is very much like the `intersection` operation above as we have a loop in lines 3 - 6 that checks each element of `set1` and checks to see if it is in `set2`. The difference between the two operations is that in the `isSubset` operation, we do not build a third `result` set. Instead, if any element in `set1` is not found in `set2`, then we return `false` since not all elements of `set1` are contained in `set2`. If we get all the way through the loop, we have checked that each element in `set1` was found in `set2` and we can return `true`; `set1` is a subset of `set2`.

```tex
function isSubset (set1, set2) returns boolean
    set1.reset()	                          (1)
    current = set1.getNext()	              (2)
    while current != null	                  (3)
        if set2.contains(current.getKey())	  (4)
            return false	                  (5)
        end if
        current = set1.getNext()	          (6)
    end while

    return true	                              (7)
end function
```
