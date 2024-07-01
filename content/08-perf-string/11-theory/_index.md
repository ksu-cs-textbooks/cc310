---
title: "Theory"
weight: 55
pre: "11. "
---

{{< youtube KII6o4G5I_U  >}}

[Video Materials](video)

## What are Strings?

Strings are data structures which store an ordered set of characters. Recall that a character can be a: letter, number, symbol, punctuation mark, or white space. Strings can contain any number and any combination of these. As such, strings can be single characters, words, sentences, and even more. 


## How do we work with Strings?
Let's refresh ourselves on how strings work, starting with the example string: `s = "Go Cats!"`.

|[]()|||||||||
|--|--|--|--|--|--|--|--|--|
| Character| G | o |  | C | a | t | s | ! |
| Index | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 |


As with other data structures, we can access elements within the string itself. Using the example above, `s[0]` would contain the character 'G', `s[1]` would contain the character 'o', `s[2]` would contain the character ' ', and so on. 

We can determine the size of a string by using length functions; in our example, the length of s would be 8. It is also important to note that when dealing with strings, null is not equivalent to "". For string `s = ""`, the length of s would be 0. However for string `s = null`, accessing the length of s would return an error that null has no length property.


We can also add to strings or append on a surface level; though it is not that simple behind the scenes. The String class is **immutable**. This means that changes will not happen directly to the string; when appending or inserting, code will create a new string to hold that value. More concisely, the state of an immutable object cannot change.

We cannot assign elements of the string directly and more broadly for any immutable object. For example, if we wanted the string from our example to be 'Go Cat!!', we cannot assign the element through `s[6] = '!'`. This would result in an item assignment error. 

{{% notice info "Try It!" %}}

For an example, consider string s = 'abc'. If we then state in code s = s + '123', this will create a new place in memory for the new definition of s. We can verify this in code by using the id() function. 

```tex
string s = 'abc'
id(s)
Output: 140240213073680 #may be different on your personal device

string s = s + '123'
id(s)
Output: 140239945470168 
```

{{% / notice %}}

While on the surface it appears that we are working with the same variable, our code will actually refer to a different one. There are many other immutable data types as well as mutable data types.

{{% notice info "Mutable vs. Immutable" %}}

On the topic of immutable, we can also discuss the converse: **mutable** objects. Being a mutable object means that the state of the object can change. In CC310, we often worked with arrays to implement various data structures. Arrays are mutable, so as we add, change, or remove elements from an array, the array changes its state to accommodate the change rather than creating a new location in memory. 

| Data Type | Immutable? |
| ---- | ---- |
| Lists | &#9744;  |
| Sets | &#9744;  |
| Byte Arrays | &#9744;  |
| Dictionaries | &#9744;  |
| Strings | &#9745; |
| Ints | &#9745; |
| Floats | &#9745; |
| Booleans | &#9745; |

{{% / notice %}}


Reference: http://people.cs.ksu.edu/~rhowell/DataStructures/strings/strings.html
