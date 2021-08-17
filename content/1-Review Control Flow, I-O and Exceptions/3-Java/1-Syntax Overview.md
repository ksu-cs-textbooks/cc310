---
title: "Syntax Overview"
weight: 5
pre: "1. "
---
Let's discuss some of the basic concepts we need to understand about the Java programming language.

## Program Structure

To begin, let's look at a simple Hello World program written in Java:

```java
public class HelloWorld{
    public static void main(String[] args){
        System.out.println("Hello World!");
    }
}
```

This program contains multiple important parts:

1. Each Java program must contain at least one class, which is declared in a file that has the same name as the class. In this case, the class is `HelloWorld`, and it will be stored in a file called `HelloWorld.java`. 
1. Class names, method names, and variable names in Java are case-sensitive. They are typically named using _camel case_, where classes are initially capitalized but methods and variables begin with a lowercase letter. 
1. The contents of a class should be directly after the class declaration, and are surrounded by curly braces `{}`.
1. Each executable Java program must include at least one `main()` method. The _method declaration_ of this main method should exactly match what is shown here. We'll discuss these keywords in more detail in a later chapter.
1. The code that will be executed when the `main()` method is called should directly follow the method declaration. As before, the contents of the method are surrounded by curly braces `{}`.
1. Each _statement_, or line of code, in the program should be followed by a semicolon `;`. 
1. To make the program readable, each _block_ of code is typically indented within the curly braces that surround it. 

Of course, this is a very brief overview for the Java programming language. To learn more, feel free to refer to the references listed below, as well as the textbook content for previous courses. 

{{% notice info %}}

# Try It!

See if you can use the code above to write your own Hello World program in the `HelloWorld.java` file that is open to the left. We'll learn how to compile and run that program on the next page. 

{{% / notice %}}

## References

* [The Java Tutorials](https://docs.oracle.com/javase/tutorial/index.html) from Oracle
* [Java Tutorial](https://www.w3schools.com/java/default.asp) from W3Schools
* [Java Tutorial](https://www.tutorialspoint.com/java/index.htm) from Tutorials Point
