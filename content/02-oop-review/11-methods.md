---
title: "Methods"
weight: 55
pre: "11. "
---

{{< youtube Cd5sEy9Svsc  >}}

We can also add methods to our classes. These methods are used either to modify the attributes of the class or to perform actions based on the attributes stored in the class. Finally, we can even use those methods to perform actions on data provided as arguments. In essence, the sky is the limit with methods in classes, so we'll be able to do just about anything we need to do in these methods. Let's see how we can add methods to our classes.

![Person UML Diagram](/images/2/2.17.p.4.personuml.png)

## Constructors

{{< youtube ck_uPDPhaV8  >}}

A _constructor_ is a special method that is called whenever a new instance of a class is created. It is used to set the initial values of attributes in the class. We can even accept parameters as part of a constructor, and then use those parameters to populate attributes in the class. 

Let's go back to the `Person` class example we've been working on and add a simple constructor to that class:

```python
class Person:
    __last_name = "Person"
    __first_name = "Test"
    __age = 25
    
    def __init__(self, last_name, first_name, age):
        self.__last_name = last_name
        self.__first_name = first_name
        self.__age = age
```

Since the constructor is an instance method, we need to add a parameter to the function at the very beginning of our list of parameters, typically named `self`. This parameter is automatically added by Python whenever we call an instance method, and it is a reference to the current _instance_ on which the method is being called. We'll learn more about this later. 

Inside that constructor, notice that we use each parameter to set the corresponding attribute, using the `self` keyword once again to refer to the current object. 

Also, since we are now defining the attributes as _instance attributes_ in the constructor, we can remove them from the class definition itself:

```python
class Person:
    
    def __init__(self, last_name, first_name, age):
        self.__last_name = last_name
        self.__first_name = first_name
        self.__age = age
```

{{% notice info "Variable Scope" %}}

We've already discussed variable scope earlier in this course. Recall that two different functions may use the same local variable names without affecting each other because they are in different scopes. 

The same applies to classes. A class may have an attribute named `age`, but a method inside of the class may also use a local variable named `age`. Therefore, we must be careful to make sure that we access the correct variable,  using the `self` reference if we intend to access the attribute's value in the current instance. Here's a short example:

```python
class Test:
  age = 15
  
  def foo(self):
    age = 12
    print(age)      # 12
    print(self.age) # 15
    
  def bar(self):
    print(self.age) # 15
    print(age)      # NameError
```

As we can see, in the method `foo()` we must be careful to use `self.age` to refer to the attribute, since there is another variable named `age` declared in that method. However, in the method `bar()` we see that `age` itself causes a `NameError` since there is no other variable named `age` defined in that scope. We have to use `self.age` to reference the attribute. 

So, we should always get in the habit of using `self` to refer to any attributes, just to avoid any unintended problems later on.

{{% / notice %}}


## Properties

{{< youtube wwnD-Ih2yWs  >}}

In Python, we can use a special decorator `@property` to define special methods, called _getters_ and _setters_, that can be used to access and update the value of private attributes.

### Getter

In Python, a _getter_ method is a method that can be used to access the value of a private attribute. To mark a getter method, we use the `@property` decorator, as in the following example:

```python
class Person:
    
    def __init__(self, last_name, first_name, age):
        self.__last_name = last_name
        self.__first_name = first_name
        self.__age = age
        
    @property
    def last_name(self):
        return self.__last_name
    
    @property
    def first_name(self):
        return self.__first_name
        
    @property
    def age(self):
        return self.__age
```

### Setter

Similarly, we can create another method that can be used to update the value of the `age` attribute:

```python
class Person:
    
    def __init__(self, last_name, first_name, age):
        self.__last_name = last_name
        self.__first_name = first_name
        self.__age = age
        
    @property
    def last_name(self):
        return self.__last_name
    
    @property
    def first_name(self):
        return self.__first_name
        
    @property
    def age(self):
        return self.__age
    @age.setter
    def age(self, value):
        self.__age = value
```

However, this method is not required in the UML diagram, so we can omit it. 

## Adding Methods

To add a method to our class, we can simply add a function declaration inside of our class. 

```python
class Person:
    
    def __init__(self, last_name, first_name, age):
        self.__last_name = last_name
        self.__first_name = first_name
        self.__age = age
        
    @property
    def last_name(self):
        return self.__last_name
    
    @property
    def first_name(self):
        return self.__first_name
        
    @property
    def age(self):
        return self.__age
        
    def happy_birthday(self):
        self.__age = self.age + 1
```

Notice that once again we must remember to add the `self` parameter as the first parameter. This method will update the private `age` attribute by one year. 

## Instantiation

{{< youtube rmvIVHuBdCw  >}}

Now that we have fully constructed our class, we can use it elsewhere in our code through the process of instantiation. In Python, we can simply call the name of the class as a method to create a new instance, which calls the constructor, and then we can use _dot-notation_ to access any attributes or methods inside of that object. 

```python
from Person import *

john = Person("Smith", "John", 25)
print(john.last_name)
john.happy_birthday()
```

Notice that we don't have to provide a value for the `self` parameter when we use any methods. This parameter is added automatically by Python based on the value of the object we are calling the methods from.
