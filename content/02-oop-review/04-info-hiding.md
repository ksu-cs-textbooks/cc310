---
title: "Information Hiding"
weight: 20
pre: "4. "
---

{{< youtube prZ8vQbJQm0  >}}

Two of the most powerful concepts in object orientation are encapsulation and information hiding. 

* _Encapsulation_ is capturing both data and behavior into a single object. 
* _Information hiding_ is restricting access to some of the data and behavior of an object. 

Encapsulation enables information hiding, and information hiding allows us to simplify the interface used to interact with an object. Instead of needing to know everything about a particular class of objects in order to use or interact with those objects. This will make our programs less complex and easier to implement and test. It also makes it easier for you to change the internal implementations of methods without affecting the rest of your program. As long as the method behaves in the same way (i.e., produces the same outputs given a given set of inputs), the rest of your program will not be affected. Thus, we see two key parts of any class:

* The **interface** to the class. Those methods and attributes that can be seen and called by an external object. 
* The **implementation** of the class. The internal representation of the attributes and implementation of methods to achieve the desired behavior. 

## Real World Example

Encapsulation and information hiding are actually all around us. Take for example, a soda vending machine. There are many internal parts to the machine. However, as a user, we care little about how the machine works or what it does inside. We need to simply know how to insert money or swipe our card and press a couple of buttons to get the soda we desire. If a repair is needed and an internal motor is replaced, we don't care whether they replaced the motor with the exact same type of motor or the new model. As long as we can still get our soda by manipulating the same payment mechanisms and buttons, we are happy. You and I care only about the interface to the machine, not the implementation hiding inside.

## Private and Public

To implement information hiding in our classes, we use visibility. In general, attributes and methods can either be _public_ or _private_. If we want and attribute or method to be part of the class interface, we define them as _public_. If we want to hide a attribute or method from external objects, we defined them as _private_. An external object may access public attributes and call public methods, which is similar to using the payment mechanism or the buttons on a soda machine. However, the internals of how the object works is hidden by _private_ attributes and methods, which are equivalent to the internal workings of the soda machine.

## Best Practices

To implement information hiding, we recommend that you declare all attributes of a class as private. Any attribute whose value should be able to be read or changed by an external object should create special "getter" and "setter" methods that access those private variables. This way, you can make changes to the implementation of the attributes without changing how it is accessed in the external object. 
