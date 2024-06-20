---
title: "Associations"
weight: 30
pre: "6. "
---

{{< youtube mNHRPclA0DI  >}}

For object `a` to be able to call a method in object `b`, object `a` must have a reference (a pointer, or the address of) object `b`. In many cases, objects `a` and `b` will be in a long-term relationship so that one or both objects will need to store the reference to the other in an attribute. When an object holds a reference to another object in an attribute, we call this a _link_. Examples of such relationships include a driver owning a car, a person living at an address, or a worker being employed by a company. 

As we discussed earlier, objects are instances of classes. To represent this in a UML class diagram, we use the notion of an _association_, which is shown as a line connecting to two classes. More precisely, a link is an instance of an association. The figure belows shows three examples of an association between class `A` and class `B`. 

![Associations in UML](/images/2/2.6.associations.png)

The top example shows the basic layout of an association in UML. The line between the two classes denotes the association itself. The diagram specifies that `ClassA` is _associated with_ `ClassB` and vice versa. We can name the association as well as place multiplicities on the relationships. The multiplicities show exactly how many links an object of one class must have to objects of the associated class. The general form a multiplicity is `n .. m`, which means that an object must store at least `n`, but no more than `m` references to other objects of the associated class; if only one number is given such as `n`, then the object must store exactly `n` references to objects in the associated class. 

There are two basic types of associations. 

* Two-way - both classes store references to the other class.
* One-way -  only one class stores a reference to its associated class.

The middle example shows a two-way association between `ClassA` and `ClassB`. Furthermore, each object of `ClassA` must have a link to exactly three objects of `ClassB`, while each `ClassB` object must have a link with exactly one `ClassA` object. (Note that the multiplicity that constrains `ClassA` is located next to `ClassB`, while the multiplicity that constrains `ClassB` is located next to `ClassA`.)

The bottom example shows a one-way association between `ClassA` and `ClassB`. In this case, `ClassA` must have links to either zero or one objects of `ClassB`. Since it is a one-way association, `ClassB` will have no links to objects of `ClassA`.
