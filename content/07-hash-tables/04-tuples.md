---
title: "Tuples"
weight: 20
pre: "4. "
---

Before we can start describing the basic hash table functions, we first need to create a way to handle key-value pairs. We generally refer to any piece of data that has two parts as a `tuple`. In the case of key-value pairs, our tuple would look like `(key, value)`. Some languages, such as Python, provide built-in support for creating tuples, while others such as Java and C# require us to create our own tuple class, which is easy to do. All we really need our `tuple` class to do is to allow us to:

1. create a tuple consisting of two objects,
2. access either of the two parts of the tuple,
3. check two tuples for equality, and
4. convert the tuple to a string.

The pseudocode for the `Tuple` class is given below. Each of the operations is simple and thus we do not discuss them individually. However, notice that the class has two attributes, `key` and `value,` that are created in the constructor. The `getKey` and `getValue` operations are used often in the code below to provide access to the internals of the tuples.

```tex
class Tuple	
    object key = null
    object value = null

    function Tuple(object k, object v)
        key = k
        value = v
    end function

    function getKey() returns string
        return key
    end function

    function getValue() returns object
        return value
    end function

    function toString() returns string
        return "(" + key.toString() + "," + value.toString() + ")"
    end function

    function equals(Object o) returns boolean
        if o is not an instance of Tuple:
            return false
        end if
        Tuple t = (Tuple)o
        return (o.key == key) AND (o.value == value)
    end function
```
