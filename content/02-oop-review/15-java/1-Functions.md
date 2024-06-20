---
title: "Functions"
weight: 5
pre: "1. "
---
{{< youtube 5LOXCJZAS40  >}}

In Java, each piece of code is broken down into _functions_, which are individual routines that we can call in our code. Let's review how to create functions in Java.

## Functions in Flowcharts & Pseudocode

The table below lists the flowchart blocks used to represent functions, as well as the corresponding pseudocode:

| Operation | Flowchart | Pseudocode |
|:---------:|:---------:|:-----------|
| Declare Function | ![Declare Function Flowchart Block](/images/2/2.17.x.1.function1.png) | <pre><code>function FOO(X)<br>    X = X + 5<br>    return X<br>end function</code></pre> |
| Call Function | ![Call Function Flowchart Block](/images/2/2.17.x.1.function2.png) | <pre><code>X = FOO(5)</code></pre> |

## Functions in Java

### Declaring Functions

{{< youtube F6YsCehtfS0  >}}

In general, a function declaration in Java needs a few elements. Let's start at the simplest case:

```java
static void foo(){
  System.out.println("Foo");
  return;
}
```

Let's break this example function declaration down to see how it works:

1. First, we use the keyword `static` at the beginning of this function declaration. That keyword allows us to use this function without creating an object first. We'll cover how to create and work with objects in a later module. For now, each function we create will need the `static` keyword in front of it, just like the `main()` function. 
1. Then, the second keyword, `void`, determines the type of data returned by the function. We use a special keyword `void` when the function does not return a value. We've already seen this keyword used in our declaration of the `main` function.
1. Next, we have the name of the function, `foo`. We can name a function using any valid identifier in Java. In general, function names in Java always start with a lowercase letter. 
1. Following the function name, we see a set of parentheses `()` that list the parameters for this function. Since there is nothing included in this example, the function `foo` does not require any parameters.
1. Finally, we see a set of curly braces `{}` that surround the code of the function itself. In this case, the function will simply print `Foo` to the terminal.
1. The function ends with the `return` keyword. Since we aren't returning a value, we aren't required to include a `return` keyword in the function. However, it is helpful to know that we may use that keyword to exit the function at any time. 

Once that function is created, we can call it using the following code:

```java
foo();
```

### Parameters and Return

{{< youtube O-vkFmelepU  >}}

In a more complex case, we can declare a function that accepts parameters and returns a value, as in this example:

```java
static int countLetters(String input, char letter){
    int output = 0;
    for(int i = 0; i < input.length(); i++){
        if(input.charAt(i) == letter){
            output++;
        }
    }
    return output;
}
```

In this example, the function accepts two parameters: `input`, which is a string, and `letter`, which is a character. It also declares that it will return an `int` value. 

We can use the parameters just like any other variable in our code. To return a value, we use the `return` keyword, followed by the value or variable containing the value we'd like to return. 

To call a function that requires parameters, we can include values as _arguments_ in the parentheses of the function call:

```java
sum += countLetters("The quick brown fox jumped over the lazy dog", 'e');
```
