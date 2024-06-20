---
title: "Attributes"
weight: 25
pre: "5. "
---
{{< youtube RzpoMdr2Fs4  >}}

Of course, our classes are not very useful at this point because they don't include any attributes or methods. Including attributes in a class is one of the simplest uses of classes, so let's start there.

![Person UML Diagram](/images/2/2.17.j.4.personuml.png)

## Adding Attributes

To add an attribute to a class, we can simply declare a variable inside of our class declaration:

```java
public class Person{
    String lastName;
    String firstName;
    int age;
}
```

That's really all there is to it! We can also add default values to these attributes by assigning a value to the variable in the same line as the declaration:

```java
public class Person{
    String lastName = "Person";
    String firstName = "Test";
    int age = 25;
}
```

However, it is very important to note that we **cannot** declare an attribute and then set the default value on a separate line. So, code such as this is not allowed:

Finally, we can add either the `public` keyword to the beginning of each of these attributes to make them available to code outside of this class, or the `private` keyword to prevent other code from accessing those attributes directly. We denote this by adding a `+` in front of the attribute in our UML diagram for public attributes, and a `-` for private attributes.  In the diagram above, each attribute is private, so we'll do that in our code:

```java
public class Person{
    private String lastName;
    private String firstName ;
    private int age;
}
```
