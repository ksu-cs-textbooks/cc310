---
title: "Static and Abstract"
weight: 40
pre: "8. "
---
The other important modifier we can use in Java is the `static` modifier. Again, we've seen this modifier each time we declare the `main` method in our programs, but we haven't really been able to discuss exactly what it means. Thankfully, we now have the knowledge we need to talk about the `static` modifier.

In essence, the `static` modifier makes an attribute or method part of the class in which it is declared instead of part of objects instantiated from that class. If we think about it, the word _static_ means "lacking in change", and that's sort of a good way to think about it. 

## Static Attributes

{{% youtube iAi_LIWyU_c %}}

First, we can use the `static` modifier with an attribute, attaching that attribute to the class instead of the instance. Here's an example:

```java
public class Stat{
  public static int x = 5;
  public int y;
  
  public Stat(int an_y){
    this.y = an_y;
  }
}
```

In this class, we've created a `static` attribute named `x`, and a normal attribute named `y`. Here's a `main()` method that will help us explore how the static keyword operates:

```java
public class Main{
 public static void main(String[] args){
   Stat someStat = new Stat(7);
   Stat anotherStat = new Stat(8);
   
   System.out.println(someStat.x);      // 5
   System.out.println(someStat.y);      // 7
   System.out.println(anotherStat.x);   // 5
   System.out.println(anotherStat.y);   // 8
   
   someStat.x = 10;
   
   System.out.println(someStat.x);      // 10
   System.out.println(someStat.y);      // 7
   System.out.println(anotherStat.x);   // 10
   System.out.println(anotherStat.y);   // 8
   
   Stat.x = 25;
   
   System.out.println(someStat.x);      // 25
   System.out.println(someStat.y);      // 7
   System.out.println(anotherStat.x);   // 25
   System.out.println(anotherStat.y);   // 8
 } 
}
```

First, we can see that the attribute `x` is set to 5 as its default value, so both objects `someStat` and `anotherStat` contain that same value. Then we can update the value of `x` attached to `someStat` to 10, and we'll see that both objects will now contain that value. That's because the value is `static`, and there is only one copy of that value for all instances of the `Stat` class. 

Finally, and most interestingly, since the attribute `x` is static, we can also access it directly from the class `Stat`, without even having to instantiate an object. So, we can update the value in that way, and it will take effect in any objects instantiated from `Stat`. 

## Static Methods

We can also do the same for static methods. 

```java
public class Stat{
  public static int x = 5;
  public int y;
  
  public Stat(int an_y){
    this.y = an_y;
  }
  
  public static int sum(int a){
    return x + a;
  }
}
```

We have now added a static method `sum()` to our `Stat` class. The important thing to remember is that a static method cannot access any non-static attributes or methods, since it doesn't have access to an instantiated object. Likewise, we cannot use the `this` keyword inside of a static method. 

As a tradeoff, we can call a static method without instantiating the class either, as in this example:

```java
public class Main{
 public static void main(String[] args){
   //other code omitted
   Stat.x = 25;
   
   Stat moreStat = new Stat(7);
   System.out.println(moreStat.sum(5));  // 30
   System.out.println(Stat.sum(5));      // 30
 }
}
```

This becomes extremely useful in our `main()` method. Since the `main()` method is always static, it can only access static attributes and methods in the class it is declared in. So, we can either create all of our additional methods in that class as `static` methods, or we can instantiate the class it is contained in.

## Abstract

Another major feature of class inheritance is the ability to define a method in a parent class, but not provide any code that implements that function. In effect, we are saying that all objects of that type must include that method, but it is up to the child classes to provide the code. These methods are called _abstract_ methods, and the classes that contain them are _abstract_ classes. Let's look at how they work!

![Vehicle UML Diagram](../../../images/2/2.17.j.8.uml.png)

### Abstract in Java

{{% youtube Sxg75nfH5q4 %}}

In the UML diagram above, we see that the `describe()` method in the `Vehicle` class is printed in italics. That means that the method should be abstract, without any code provided. To do this in Java, we simply must use the `abstract` keyword on both the method and the class itself:

```java
public abstract class Vehicle{
  
  private String name;
  protected double speed;
 
  public String getName(){ return this.name; }
  
  protected Vehicle(String name){
    this.name = name;
    this.speed = 1.0;
  }
 
  
  public double move(double distance){
    System.out.println("Moving");
    return distance / this.speed;
  }
  
  public abstract String describe();
  
}
```

Notice that the keyword `abstract` goes after the security modifier, but before the `class` keyword on a class declaration and the return type on a method declaration.  

In addition, since we have declared the method `describe()` to be abstract, we must place a semicolon after the method declaration, without any curly braces. This is because an abstract method cannot include any code. 

Now, any class that inherits from the `Vehicle` class must provide an implementation for the `describe()` method. If it does not, that class must also be declared to be abstract. So, for example, in the UML diagram above, we see that the `MotorVehicle` class does not include an implementation for `describe()`, so we'll also have to make it abstract. 

We can also declare a class to be abstract without including any abstract methods. By doing so, it prevents the class from being instantiated directly. Instead, the class can only be inherited from, and those child classes can choose to be instantiated by omitting the `abstract` keyword.
