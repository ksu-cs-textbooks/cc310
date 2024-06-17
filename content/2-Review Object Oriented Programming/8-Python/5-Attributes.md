---
title: "Attributes"
weight: 25
pre: "5. "
---
{{% youtube 9ZX2RBcsRfc %}}

Of course, our classes are not very useful at this point because they don't include any attributes or methods. Including attributes in a class is one of the simplest uses of classes, so let's start there.

![Person UML Diagram](/images/2/2.17.p.4.personuml.png)

## Adding Attributes

To add an attribute to a class, we can simply declare a variable inside of our class declaration:

```python
class Person:
    last_name = "Person"
    first_name = "Test"
    age = 25
```

That's really all there is to it! These are _static attributes_ or _class attributes_ that are shared among all instances of the class. On the next page, we'll see how we can create _instance attributes_ within the class's constructor.

Finally, we can make these attributes private by adding two underscores to the variable's name. We denote this on our UML diagram by placing a minus `-` before the attribute or method's name. Otherwise, a `+` indicates that it should be public. In the diagram above, each attribute is private, so we'll do that in our code:

```python
class Person:
    __last_name = "Person"
    __first_name = "Test"
    __age = 25
```

Unfortunately, Python does have a way to get around these restrictions as well. Instead of referencing `__last_name`, we can instead reference `_Person__last_name` to find that value, as in this example:

```python
ellie = Person("Jonson", "Ellie", 29)
ellie._Person__last_name = "Jameson"
print(ellie.last_name) # Jameson
```

Behind the scenes, Python adds an underscore `_` followed by the name of the class to the beginning of any class attribute or method that is prefixed with two underscores `__`. So, knowing that, we can still access those attributes and methods if we want to. Thankfully, it'd be hard to do this accidentally, so it provides some small level of security for our data. 
