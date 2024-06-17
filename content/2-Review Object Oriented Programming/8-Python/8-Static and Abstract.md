---
title: "Static and Abstract"
weight: 40
pre: "8. "
---
## Static

Many programming languages include a special keyword `static`. In essence, a `static` attribute or method is part of the class in which it is declared instead of part of objects instantiated from that class. If we think about it, the word _static_ means "lacking in change", and that's sort of a good way to think about it. 

In a UML diagram, static attributes and methods are denoted by underlining them.

### Static Attributes

{{% youtube T6aHU60uY2A %}}

In Python, any attributes declared outside of a method are _class attributes_, but they can be considered the same as _static attributes_ until they are overwritten by an instance. Here's an example:

```python
class Stat:
    x = 5     # class or static attribute
  
    def __init__(self, an_y):
        self.y = an_y # instance attribute
```

In this class, we've created a _class attribute_ named `x`, and a normal attribute named `y`. Here's a `main()` method that will help us explore how the static keyword operates:

```python
from Stat import *

class Main:
  
    def main():
        some_stat = Stat(7)
        another_stat = Stat(8)

        print(some_stat.x)     # 5
        print(some_stat.y)     # 7 
        print(another_stat.x)  # 5
        print(another_stat.y)  # 8

        Stat.x = 25           # change class attribute for all instances

        print(some_stat.x)     # 25
        print(some_stat.y)     # 7 
        print(another_stat.x)  # 25 
        print(another_stat.y)  # 8

        some_stat.x = 10      # overwrites class attribute in instance

        print(some_stat.x)     # 10 (now an instance attribute)
        print(some_stat.y)     # 7 
        print(another_stat.x)  # 25 (still class attribute)
        print(another_stat.y)  # 8

if __name__ == "__main__":
    Main.main()
```

First, we can see that the attribute `x` is set to 5 as its default value, so both objects `some_stat` and `another_stat` contain that same value. Interestingly, since the attribute `x` is static, we can access it directly from the class `Stat`, without even having to instantiate an object. So, we can update the value in that way to 25, and it will take effect in any objects instantiated from `Stat`.

Below that, we can update the value of `x` attached to `some_stat` to 10, and we'll see that it now creates an _instance attribute_ for that object that contains 10, overwriting the previous _class attribute_. The value attached to `another_stat` is unchanged. 

### Static Methods

Python also allows us to create _static methods_ that work in a similar way:

```python
class Stat:
    x = 5     # class or static attribute
  
    def __init__(self, an_y):
        self.y = an_y # instance attribute
  
    @staticmethod
    def sum(a):
        return Stat.x + a
```

We have now added a static method `sum()` to our `Stat` class. To create a static method, we place the `@staticmethod` _decorator_ above the method declaration. We haven't learned about decorators yet, but they allow us to tell Python some important information about the code below the decorator. 

In addition, it is important to remember that a static method cannot access any non-static attributes or methods, since it doesn't have access to an instantiated object in the `self` parameter. 

As a tradeoff, we can call a static method without instantiating the class either, as in this example:

```python
from Stat import *

class Main:
  
    @staticmethod
    def main():
        # other code omitted
        Stat.x = 25
    
        moreStat = Stat(7)
        print(moreStat.sum(5))  # 30
        print(Stat.sum(5))      # 30

if __name__ == "__main__":
    Main.main()
```

This becomes extremely useful in our `main()` method. Since we aren't instantiating our `Main` class, we can use the decorator `@staticmethod` above the method to clearly mark that it should be considered a static method. 

## Abstract

{{% youtube X21IFfio_h0 %}}

Another major feature of class inheritance is the ability to define a method in a parent class, but not provide any code that implements that function. In effect, we are saying that all objects of that type must include that method, but it is up to the child classes to provide the code. These methods are called _abstract_ methods, and the classes that contain them are _abstract_ classes. Let's look at how they work!

![Vehicle UML Diagram](/images/2/2.17.p.8.uml.png)

### Abstract in Python

In the UML diagram above, we see that the `describe()` method in the `Vehicle` class is printed in italics. That means that the method should be abstract, without any code provided. To do this in Python, we simply inherit from a special class called `ABC`, short for "Abstract Base Class," and then use the `@abstractmethod` decorator:

```python
from abc import ABC, abstractmethod

class Vehicle(ABC):
  
    def __init__(self, name):
        self.__name = name
        self._speed = 1.0
    
    @property
    def name(self):
        return self.__name
    
    def move(self, distance):
        print("Moving");
        return distance / self._speed;
  
    @abstractmethod
    def describe(self):
        pass
```

Notice that we must first import both the `ABC` class and the `@abstractmethod` decorator from a library helpfully called `ABC`. Then, we can use `ABC` as the parent class of our class, and update each method using the `@abstractmethod` decorator before the method, similar to how we've already used `@staticmethod` in an earlier module. 

In addition, since we have declared the method `describe()` to be abstract, we can either add some code to that method that can be called using `super().describe()` from a child class, or we can simply choose to use the `pass` keyword to avoid including any code in the method.

Now, any class that inherits from the `Vehicle` class must provide an implementation for the `describe()` method. If it does not, that class must also be declared to be abstract. So, for example, in the UML diagram above, we see that the `MotorVehicle` class does not include an implementation for `describe()`, so we'll also have to make it abstract. 

Of course, that means that we'll have to inherit from both `Vehicle` and `ABC`. In Python, we can do that by simply including both classes in parentheses after the subclass name, separated by a comma.
