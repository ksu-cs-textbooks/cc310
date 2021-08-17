---
title: "Hash Tables"
weight: 30
pre: "6. "
---
{{% youtube 3l7NGg0YsBk %}}

## Hash Tables

![Hash Table](../../images/12/12.6.hashtable.svg)

Analyzing the performance of a hash table is a bit trickier than the other data structures, mainly due to how a hash table tries to use its complex structure to get a "best of both worlds" performance outcome.

For example, consider the insert operation. In the best case, the hash table has a capacity that is large enough to guarantee that there are not any hash collisions. Each entry in the array of the hash table will be an empty list and inserting an element into an empty list is done in constant time, so the whole operation runs in the order of constant time.

The worst case for inserting an item into a hash table would be when every element has the same hash, so every element in the hash table is contained in the same list. In that case, we must iterate through the entire list to make sure the key has not already been used, which would be in the order of $N$ time. 

Thankfully, if we properly design our hash table such that the capacity is much larger than our expected size, and the hash function we use to hash our keys results in a properly distributed hash, this worst case scenario should happen very rarely, if ever. Therefore, our expected performance should be closer to constant time.

One important thing to remember, however, is that each operation in a hash table requires computing the hash of the key given as input. Therefore, while some operations may run in constant time, if the action of computing the hash is costly, the overall operation may run very slowly. 

The analysis of the operation to access a single element in a hash table based on a given key is similar. If the hash table elements are distributed across the table, then each list should only contain a single element. In that case, we can just compute the hash of the key and determine if that key has been used in a single operation, which runs in the order of constant time.

In the worst case, however, we once again have the situation where all the elements have been placed in the same linked list. We would need to iterate through each element to find the one we are looking for. In that case, the operation would run in the order of $N$ time.

The operation for finding a specific element in a hash table is a bit unique. In this case, we are discussing looking for a particular value, not necessarily a particular key. That operation is discussed in the previous paragraph. For the operation, the only possible way forward is to iterate through each list in the hash table and perform a linear search for the requested value, which will always run in order $N$ time.

Finally, if we want to delete a single element from a hash table based on a given key, the analysis is the same as inserting or finding an element. In the best case, it runs in the order of constant time, but the worst case runs in the order of N time since we must iterate through an entire list of $N$ elements. 

Even though a hash table has some very poor performance in the worst case, as discussed earlier those worst case situations are very rare, and as long as we are careful about how we manage the capacity of our hash table and how we compute the hash of our objects, we can expect to see operations running in near constant time during normal usage. 
