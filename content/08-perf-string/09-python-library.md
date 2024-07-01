---
title: "Python Standard Types"
weight: 45
pre: "9. "
---

{{< youtube B4vL-QLci8w  >}}

Both Java and Python include standard implementations of each of the data structures we have learned about in this course. While it is very useful and interesting from an academic perspective to build our own linked lists and hash tables, in practice we would rarely do so. In this section, we will briefly introduce the standard library versions of each data structure and provide references to where we can find more information about each one and how to use them. 

## Python

Python includes many useful data structures as built-in data types. We can use them to build just about any structure we need quickly and efficiently. The [Python Tutorial](https://docs.python.org/3/tutorial/datastructures.html) has some great information about data structures in Python and how we can use them.

Python includes several data types that are grouped under the heading of [sequence data types](https://docs.python.org/3/library/stdtypes.html#sequence-types-list-tuple-range), and they all share many operations in common. We'll look at two of the sequence data types: tuples and lists. 

### Tuples

While we have not directly discussed tuples often, it is important to know that Python natively supports tuples as a basic data type. In Python, a [tuple](https://docs.python.org/3/library/stdtypes.html#tuple) is simply a combination of a number of values separated by commas. They are commonly placed within parentheses, but it is not required. 

We can directly access elements in a tuple using the same notation we use for arrays, and we can even unpack tuples into multiple variables or return them from functions. Tuples are a great way to pass multiple values as a single variable.

```python
tuple1 = 'a', 'b', 'c'
print(tuple1)  # ('a', 'b', 'c')

tuple2 = (1, 2, 3, 4)
print(tuple2)  # (1, 2, 3, 4)
print(tuple2[0]) # 1
a, b, c, d = tuple2
print(d) # 4
```

### Lists

Python's default data structure for sequences of data is the [list](https://docs.python.org/3/library/stdtypes.html#list). In fact, throughout this course, we have been using Python lists as a stand-in for the arrays that are supported by most other languages. Thankfully, lists in Python are much more flexible, since they can be dynamically resized, sliced, and iterated very easily. In terms of performance, a Python list is roughly equivalent to an array in other languages. We can access elements in constant time when the index is known, but inserting and removing from the beginning of the list runs in order of $N$ time since elements must be shifted backwards. This makes them a poor choice for queues and stacks, where elements must be added and removed from both ends of the list. 

```python
list1 = ['a', 'b', 'c']
print(list1) # ['a', 'b', 'c']
print(list1[1:2]) # ['b', 'c']
```

### Deque

The Python [Collections](https://docs.python.org/3.8/library/collections.html) library contains a special class called a deque (pronounced "deck", and short for "double ended queue") that is a linked list-style implementation that provides much faster constant time inserts and removals from either end of the container. In Python, it is recommended to use the deque data structure when implementing stacks and queues. 

In a deque, the ends are referred to as "right" and "left", so there are methods `append()` and `pop()` that impact the right side of the container, and `appendleft()` and `popleft()` that modify the left side. We can use a combination of those methods to implement both a Stack and a Queue using a deque in Python.

```python
from collections import deque

# Stack
stack = deque()
stack.append(1)
stack.append(2)
print(stack[-1]) # 2 (peek right side)
print(stack.pop()) # 2
print(stack.pop()) # 1

# Queue
queue = deque()
queue.append(1)
queue.append(2)
print(queue[0]) # 1 (peek left side)
print(queue.popleft()) # 1
print(queue.popleft()) # 2
```

### Dictionaries

Python also implements a version of the class Map data structure, called a [dictionary](https://docs.python.org/3/tutorial/datastructures.html#dictionaries). In Python, a dictionary stores key-value pairs, very similarly to how associative arrays work in other languages. Behind the scenes, it uses a hashing function to efficiently store and retrieve elements, making most operations run in near constant time. 

The one limitation with Python dictionaries is that only hashable data types can be used as keys. We cannot use a list or a dictionary as the key for a dictionary in Python. Thankfully, strings, numbers, and most objects that implement a `__hash__()` and `__eq__()` method can be used.

```python
dict = {'name': 123, 'test': 321}
print(dict['name']) # 123 (get a value)
dict['date'] = 456 # (add a new entry)
print('name' in dict) # True (search for entry)
```

### Sets

Python also includes a built in data type to represent a [set](https://docs.python.org/3/tutorial/datastructures.html#sets). Just like we saw with our analysis, Python also uses a hash-based implementation to allow us to quickly find elements in the set, and therefore does not keep track of any ordering between the elements. We can easily add or remove elements, and Python uniquely allows us to use the binary operators to compute several set operations such as union and intersection.

```python
set1 = {1, 3, 5, 7, 9}
set2 = {2, 3, 5, 7}
print(2 in set1) # False (check for membership)
print(2 in set2) # True (check for membership)

print(set1 – set2) # {1, 9} (set difference)
print(set1 | set2) # {1, 3, 5, 7, 9, 2} (union)
print(set1 & set2) # {3, 5, 7} (intersection)
```
