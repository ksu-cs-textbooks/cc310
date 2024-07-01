---
title: "1 Java Standard Library"
weight: 5
pre: "1. "
---
{{< youtube O82V_nPufjc  >}}

Both Java and Python include standard implementations of each of the data structures we have learned about in this course. While it is very useful and interesting from an academic perspective to build our own linked lists and hash tables, in practice we would rarely do so. In this section, we will briefly introduce the standard library versions of each data structure and provide references to where we can find more information about each one and how to use them.

## Java

In Java, most common data structures are part of the Java Collections Framework. It includes interfaces, implementations, and a variety of algorithms that can be used to do almost any common operation with data structures. You can find more information on the [Java Tutorials]( https://docs.oracle.com/javase/tutorial/collections/index.html) website.

### ArrayList

The most useful Java collection is the [ArrayList]( https://docs.oracle.com/javase/8/docs/api/java/util/ArrayList.html). It performs very similarly to an array in most ways. Accessing an element in an ArrayList with an index runs in constant time, and adding new elements to the end of the container can also be done very quickly. In fact, most commonly used list operations run in constant time, and the memory and performance overhead that comes with using an ArrayList is very small. 

ArrayLists in Java also support [Generics](https://docs.oracle.com/javase/tutorial/java/generics/index.html), which is a fancy way of saying that we can define the data types our collection should store and return, instead of just using Objects like we did in this course. We place this in angled brackets `<>` when we declare and instantiate the structure. This helps make our code easier to understand and can make it much easier to detect and correct type errors when we accidentally try to store an incorrect type in an ArrayList.

```java
import java.util.ArrayList;

public class AList{
	public static void main(String[] args){
        ArrayList<Integer> alist = new ArrayList<Integer>();
        alist.add(1);
        alist.add(2);
        System.out.println(alist.get(0) + alist.get(1));
	}
}
```

### LinkedList

Java also includes an implementation of a [LinkedList](https://docs.oracle.com/javase/8/docs/api/java/util/LinkedList.html) data structure. This structure also performs very similarly to the one we built in this class. Inserting or removing elements from the beginning and the end are constant time, as well as removing items from the middle of the list, provided we are using an iterator to find them. 

LinkedLists in Java are also the ideal choice for implementing both Stacks and Queues because of the constant time operations for inserting and removing elements from the beginning and end of the list. In fact, it even includes the `push()`, `pop()` and `peek()` methods to simulate a stack, and uses `offer()` and `poll()` in place of `enqueue()` and `dequeue()` for queues. 

LinkedLists in Java also support [Generics](https://docs.oracle.com/javase/tutorial/java/generics/index.html). 
According to the Java documentation, when faced with a choice between ArrayList and LinkedList implementations of a particular container, in most cases the ArrayList implementation may be more performant. The exception would be when working with stacks and queues, in which case a LinkedList may work a bit better. When in doubt, they suggest trying the program with both structures and seeing which one performs better. 

```java
import java.util.LinkedList;

public class LList{
	public static void main(String[] args){
        LinkedList<Integer> llist = new LinkedList<Integer>();
        
        //Stack
        llist.push(new Integer(1));
        llist.push(new Integer(2));
        System.out.println(llist.peek());
        llist.pop();
        System.out.println(llist.pop());

        //Queue
        llist.offer(new Integer(1));
        llist.offer (new Integer(2));
        System.out.println(llist.peek());
        llist.poll();
        System.out.println(llist.poll());	
    }
}
```

### Hash Tables

Java includes three different implementations of the generic Map data structure, which stores a key-value pair. Two of them offer the ability to sort the keys or keep track of the order that elements were added to the structure, but we won't review those here. The fastest is the [HashMap](https://docs.oracle.com/javase/8/docs/api/java/util/HashMap.html), which doesn't guarantee anything about the ordering of the keys or values but will give the best performance overall. 

HashMaps in Java once again have support for [Generics](https://docs.oracle.com/javase/tutorial/java/generics/index.html), which allows us to define the data type for both the keys and the values stored in the HashMap. This also simplifies things since we do not have to manage the creation of tuples outside of the collection. Instead, it is all handled internally.

```java
import java.util.HashMap;

public class HMap{
	public static void main(String[] args){
        HashMap<String, Integer> hmap = new HashMap<String, Integer>();
        hmap.put(“Test”, new Integer(123));
        hmap.put(“Name”, new Integer(321));
        System.out.println(hmap.get(“Test”));
        hmap.remove(“Name”);
        System.out.println(hmap.containsKey(“Name”));
    }
}
```

### Sets

Java also includes a very fast implementation of the Set data structure called [HashSet](https://docs.oracle.com/javase/8/docs/api/java/util/HashSet.html). It uses hashing to guarantee that each element is unique, and does not guarantee any particular ordering of the elements in the set. In fact, behind the scenes, the HashSet data structure uses a HashMap to store the data!

Unfortunately, the Set data structures in Java do not include straightforward implementations of many of the set operations, such as union, intersection, and subset. However, we can use a few of the included methods such as `retainAll()` and `removeAll()` to simulate those operations.  

As with all the other Java data structures, HashSets also supports [Generics](https://docs.oracle.com/javase/tutorial/java/generics/index.html), so we can define the data type it should be storing when we create it.

```java
import java.util.HashSet;

public class HSet{
	public static void main(String[] args){
        HashSet<String> hset = new HashSet<String>();
        hset.add(“Test);
        hset.add(“Name”);
        System.out.println(hset.contains(“Name”));
        hset.remove(“Name”);
        System.out.println(hset.containsKey(“Name”));
    }
}
```

### Algorithms

Finally, we should also review the Java [Collections](https://docs.oracle.com/javase/8/docs/api/java/util/Collections.html) class. It contains many static methods that we can use to work with the various collections we discussed above. For example, the Collections class includes methods for sorting a collection, finding the minimum or maximum value, determining if two collections are disjoint, and more. 

Many of them are described in detail on the [Algorithms](https://docs.oracle.com/javase/tutorial/collections/algorithms/index.html) page of the Collections tutorial. 

Java also includes a special [Arrays](https://docs.oracle.com/javase/8/docs/api/java/util/Arrays.html) class that contains methods for manipulating raw arrays in a similar way. 

Both of these classes are very useful to work with, since they help us avoid "reinventing the wheel" when we want to perform many common operations with our data. 
