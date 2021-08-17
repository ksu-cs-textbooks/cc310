---
title: "Classes and Objects"
weight: 15
pre: "3. "
---
{{% youtube OcBIBGdkNTs %}}

As you might guess from its name, object-oriented programming languages are made to create and manipulate entities called _objects_. But what exactly are these objects? Objects were created to help decompose large complex programs with a lot of complex data into manageable parts. 

{{% notice info %}}

# Object

An **object** is a programming entity that contains related data and behavior.

{{% / notice %}}

A good example of an object is dog. But not just any dog, or all dogs, but a specific dog. Each dog has specific characteristics that are captured as data such as their name, their height, their weight, their breed, their age, etc. We call these characteristics _attributes_ and all dogs have the same type of attributes, although the values of those attributes may be unique.  And generally, all dogs exhibit the same behaviors, or _methods_. Almost all dogs can walk, run, bark, eat, etc.

So, how do we define the basic attributes and behaviors of a dog? We probably start with some kind of idea of what a dog is. How do we describe dogs in general. In object orientation we do that through classes. 

{{% notice info %}}

# Class
 
A **class** is a blueprint for an object. 

{{% / notice %}}

What do we use blueprints for? Well, when we are building a physical structure such as a home or office building, an architect first creates a blueprint that tells the builder what to build and how everything should fit together. That is essentially what a class does. A class describes the types of _attributes_ and _methods_ that an object of that class will have. 

Then to create objects, we say we create an instance of a class by calling the class's _constructor_ method, which creates an object instance in memory and makes sure it's attributes are properly created. Once the object has been created, the methods defined by the class can be used to manipulate the attributes and internal data of the object. 
