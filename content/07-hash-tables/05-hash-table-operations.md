---
title: "Hash Table Operations"
weight: 25
pre: "5. "
disableMathJax: false
---

{{% notice note "Hash Table Operations" %}}

You won't be asked to implement any of these operations since we will just use the built-in class in our chosen language. However, we want you to se behind the scenes and understand how a hash table is implemented directly in code. 

{{% /notice %}}

{{< youtube tpEPdUwW4M8  >}}

The `HashTable` class has three attributes that provide the basic data structure and parameters we need to efficiently manage our table. 

1. `size` - captures the number of tuples stored in the table. It is initialized to `0` in line 11 of the constructor.
1. `loadFactor` - is the load factor used to determine when to increase the capacity of the array. It is initialized to `0.75` in line 12 of the constructor.
1. `hashTable` - is an array of doubly linked lists. The array is actually created in line 7 of the constructor and the doubly linked lists for each location in the array are created in the loop in lines 8 and 9 of the constructor.

{{< highlight lineNos="true" lineNoStart="1" type="py" >}}
class HashTable
    int size
    double loadFactor = 0.75
    doubleLinkedList[] hashTable

    function HashTable()
        hashTable = new doubleLinkedList[16]
        for i = 0 to hashTable.length
            hashTable[i] = new doubleLinkedList()
        end for
        size = 0
        loadFactor = 0.75
    end function
{{< /highlight >}}

## Compute Index

We assume we are using the language-specific hash code function to actually generate our hash code. However, we need to convert that number (typically a very large integer) to an index for our array, which has a limited capacity. Therefore, we use the modulo function in line 2 to convert the hash code into the range of `0` to the capacity of the array. The `computeIndex` operation runs in constant time.

{{< highlight lineNos="true" lineNoStart="1" type="py" >}}
function computeIndex(object key) returns integer
    return hashCode(key) % getCapacity()
end function
{{< /highlight >}}
        
## Put

The `put` operation is an important hash table operation, whose goal is to place a key-value pair into the right linked list. We start by calling `computeIndex` to find which linked list we should store the key-value pair in, which we can access using `hashTable[index]`. Next, we check to see if the `key` has already been stored in the table by iterating through the list found at that location in the table. If the `key` has already been stored, we should update the value in that tuple to be the new value in line 9 and return on line 10. If the `key` isn't found, then we actually store the key-value pair in the table by calling the `append` operation for the `hashTable[index]` linked list on line 15. Notice, we create a new `Tuple` using the `key` and `value` input parameters before we call append. Since we successfully added the new tuple, we increment the `size` attribute to keep track of the number of tuples stored in the table.

{{< highlight lineNos="true" lineNoStart="1" type="py" >}}
function put(object key, object value)
    index = computeIndex(key)

    hashTable[index].reset()
    current = hashTable[index].getNext()

    while current != null
        if current.key ==  key
            current.value = value
            return
        end if
        current = hashTable[index].getNext()
    end while

    hashTable[index].append(new Tuple(key, value))
    size = size + 1

    if size/capacity > loadFactor
        doubleCapacity()
    end if
end function
{{< /highlight >}}  
        
Since we have added a new tuple to the table, we need to check to see if the size of the table exceeds our load factor. Therefore, in line 18, we check to see if the value of `size/capacity` exceeds our `loadFactor`. If it does, we call the `doubleCapacity` operation to double the capacity of our array and rehash the table. The `doubleCapacity` operation is defined below. 

Since we are looping through a list of elements in the hash table, it can be difficult to analyze the running time of this method. So, we have to look at both the best case and worst case scenario. In the best case, the linked list is empty, so the entire operation runs in constant time. As long as we have a good hash function and the keys are equally distributed across the hash table, this should be the case. 

However, if the hash function is poor, it could cause all of the elements in the hash table to be placed in the same list. In that case, the operation would run on the order of $N$ time, since it would have to iterate across all elements in the list. 

## Get 

The `get` operation is another important hash table operation, whose goal is to retrieve (without deleting) a key-value pair from the table. Like the `put` operation, the first thing we need to do is to compute the index of the `key` we are looking for in line 2. Once we know the `index`, we call the `reset` operation on the `hashTable[index]` linked list so we can call the `getNext` iterator function in line 4. Lines 6 - 8 are a loop that walks through each key-value pair in the linked list. If we find the `key` we are looking for in line 7, we return `true` and the operation ends. If we do not find the `key`, we call the `getNext` function to get the next element in the linked list. If we end up going through the entire loop until `current != null` becomes false, we fall out of the loop and return null in line 13, indicating that we did not find `key` in the table.

{{< highlight lineNos="true" lineNoStart="1" type="py" >}}
function get(object key) returns object
    index = computeIndex(key)
    hashTable[index].reset()
    current = hashTable[index].getNext()

    while current != null
        if current.key ==  key
            return current.value
        end if
        current = hashTable[index].getNext()
    end while

    return null
end function
{{< /highlight >}}

As discussed above, although we do end up looping through one of the linked lists in the hash table, these lists are much, much smaller than the overall size of the hash table under most normal circumstances. Thus, we say that the `get` operation runs in constant time in the best case. 

## Remove

The `remove` operation is much like the `get` operation above, except that when we find the `key` we are searching for, we remove the key-value pair from the appropriate linked-list and return the `value` to the calling function. The only real difference in the operations lies in the loop intervals in lines 8 and 9. Here, when we find the `key` in the list, we call the `removeCurrent` operation to remove the key-value pair from the linked list and then decrement size by 1. Line 10 then returns `current.value`.

{{< highlight lineNos="true" lineNoStart="1" type="py" >}}
function remove(object key) returns object
    index = computeIndex(key)
    hashTable[index].reset()
    current = hashTable[index].getNext()

    while current != null
        if current.key == key
            hashTable[index].removeCurrent()
            size = size – 1
            return current.value
        end if
        current = hashTable[index].getNext()
    end while

    return null
end function
{{< /highlight >}}

Like the `get` operation above, we loop through one of the linked lists in the hash table. However, given the relatively small size of the list, we assume the `remove` operation runs in constant time in the best case.

## Contains Key

The `containsKey` operation returns a Boolean value based on whether we find the requested `key` in the table. Since the `get` operation already finds the key-value pair associated with a given `key`, we simply call `get` and then compute whether the key-value pair returned from `get` exists to compute the `containsKey` return value. The `containsKey` operation runs in constant time in the best case.

{{< highlight lineNos="true" lineNoStart="1" type="py" >}}
function containsKey(object key) returns boolean
    return get(key) != null
end function
{{< /highlight >}}
        
## Contains Value

The `containsValue` operation is not as simple as `containsKey` since we don't already have an operation to use  to search for a value in our hash table. Since we are not given a `key` to search for, we cannot use the `computeIndex` to tell us which linked list to search for our `value`. Therefore, we need to start at the beginning of our array and loop through each element, searching each of the linked lists stored there for our `value`.

Line 1 is our outside loop that walks through each linked list stored in our array. Within that  loop, we follow the same search process we used in the `get` operation to search through `hashTable[i]`. We set up the iterator in lines 3 and 4 and then walk through the linked list in the loop in lines 6 - 9. The only difference in this search process is what we are searching for. In line 7, instead of checking if the keys are equal, we check to see if the values are equal. If they are, we return true. However, if we do not find the value somewhere in the table, we must search through every key-value pair in the table, thus the time complexity for `containsValue` is order $N$.

{{< highlight lineNos="true" lineNoStart="1" type="py" >}}
function containsValue(object value) returns boolean 
    for i = 0 to getCapacity()
        hashTable[i].reset()
        current = hashTable[i].getNext()

        while current != null
            if current.value == value
                return true
            current = hashTable[i].getNext()
        end while
    end for

    return false
end function
{{< /highlight >}}

## Get Size

The `getSize` function is very simple. It simply returns the HashTable class' `size` attribute.

{{< highlight lineNos="true" lineNoStart="1" type="py" >}}
function getSize() returns integer
    return size
end function
{{< /highlight >}}

## Get Capacity

Like the `getSize` function, `getCapacity` simply returns the length of the `hashTable` array.

{{< highlight lineNos="true" lineNoStart="1" type="py" >}}
function getCapacity() returns integer
    return length of the hashTable array
end function
{{< /highlight >}}

## Is Empty

The `isEmpty` operation simply returns the Boolean value of whether or not the `size` attribute is 0. 

{{< highlight lineNos="true" lineNoStart="1" type="py" >}}
function isEmpty() returns boolean
    return size == 0
end function
{{< /highlight >}}

## Copy

The `copy` operation is similar to the `containsValue` operation in that it must walk through the entire hash table to get all the key-value pairs in the table and `put` them into the new hash table. Line 2 creates the new empty hash table, which we call `copy`. 

The `for` loop in line 4 walks through the `hashTable` array, allowing us to access each linked list using `hashTable[i]`. Within the loop we use the linked list iterator functions (lines 5, 6, and 10) to walk through each key-value pair in the linked lists. For each key-value pair, we call `copy.put` to insert that key-value pair into the `copy` hash table. Once we have completed both loops, we return the copy in line 14. Like the `containsValue` operation, since we walk through each key-value pair in the hash table, the `copy` operation runs in order $N$ time.

{{< highlight lineNos="true" lineNoStart="1" type="py" >}}
function copy() returns HashTable
    HashTable copy = new HashTable()

    for i = 0 to getCapacity()
        hashTable[i].reset()
        current = hashTable[i].getNext()

        while current != null
            copy.put(current.key, current.value)
            current = hashTable[i].getNext()
        end while
    end for

    return copy
end function
{{< /highlight >}}

## To String

The `toString` operation is almost identical to the `copy` operation above, except that instead of inserting each key-value pair into a second hash table, we append the string representation of each key-value pair to an `output` string. In fact, the only differences to the pseudocode come in lines 2, 9, and 10. Line 2 creates a new empty string and line 13 returns that string after walking through the hash table. Finally, line 9 is where we append the current key-value pair's string representation to the `output` string. We also append a comma to separate the key-value pairs in `output`. Like the `copy` operation, the `toString` operation runs in order $N$ time.

{{< highlight lineNos="true" lineNoStart="1" type="py" >}}
function toString() returns string
    string output = null

    for i = 0 to getCapacity()
        hashTable[i].reset()
        current =  hashTable[i].getNext()

        while current != null
            output += current.toString() + ", "
            current =  hashTable[i].getNext()
        end while
    end for
    return output
end function
{{< /highlight >}}

## Double Capacity

The `doubleCapacity` operation is similar to the same operations for the array-based stack and queue implementations that we covered earlier. First, we create a new array with twice the capacity of the existing `hashTable`. Next, we "rehash" each of the key-value pairs in `hashTable` into the new table. Finally, we point the `hashTable` attribute at the new table.

The implementation of this process is captured in the following pseudocode. In line 2, we double the size of `capacity`. It is important to update `capacity` first so we can use the new value when creating the new hash table array. It is especially important to use this new capacity when calculating the indexes for key-value pairs in the new table.

{{< highlight lineNos="true" lineNoStart="1" type="py" >}}
function doubleCapacity()
    capacity = capacity * 2
    doubleLinkedList[] newTable = new doubleLinkedList[getCapacity()]

    for i = 0 to getCapacity()
        newTable[i] = new doubleLinkedList()
    end for

    for i = 0 to getCapacity() / 2
        hashTable[i].reset()
        current = hashTable[i].getNext()

        while current != null
            index = computeIndex(current.key)
            newTable[index].append(current)
            current = hashTable[i].getNext()
        end while
    end for

    hashTable = newTable
end function
{{< /highlight >}}

Line 2 creates a new array called `newTable` with twice the capacity of the existing table. In lines 5 and 6, we create a new doubly linked list for each element of `newTable`.  Then, in lines 9 - 16 we employ the same looping structure used above in `copy` and `toString` to walk through each key-value pair in `hashTable`. Then for each key-value pair, we compute its new `index` and then append the key-value pair to the linked list at `hashTable[index]`.  Once we have completed the copying process, we fall out of the loop. Our final action is to point the `hashTable` attribute at `newTable`. Like the `copy` and `toString` operations, the run time of `doubleCapacity` is order $N$.

## Iterator Operations

While we do not present the iterator operations here, they are useful operations for hash tables. They are implemented similarly to the other iterator functions we have studied, except that in order to walk through the entire hash table we need to use nested loops where the outside loop walks through the array and the internal loop walks through each linked list. This is very similar to the looping structure in `doubleCapacity` above.
