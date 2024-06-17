---
title: "Functions"
weight: 5
pre: "1. "
---
{{% youtube 5LOXCJZAS40 %}}

In Python, we can break our programs up into individual _functions_, which are individual routines that we can call in our code. Let's review how to create functions in Python.

## Functions in Flowcharts & Pseudocode

The table below lists the flowchart blocks used to represent functions, as well as the corresponding pseudocode:

| Operation | Flowchart | Pseudocode |
|:---------:|:---------:|:-----------|
| Declare Function | ![Declare Function Flowchart Block](/images/2/2.17.x.1.function1.png) | <pre><code>function FOO(X)<br>    X = X + 5<br>    return X<br>end function</code></pre> |
| Call Function | ![Call Function Flowchart Block](/images/2/2.17.x.1.function2.png) | <pre><code>X = FOO(5)</code></pre> |

## Functions in Python

### Declaring Functions

{{% youtube NNKPa8fLz9E %}}

In general, a function definition in Python needs a few elements. Let's start at the simplest case:

```python
def foo():
  print("Foo")
  return
```

Let's break this example function definition down to see how it works:

1. First, we use the keyword `def` at the beginning of this function definition. That keyword tells Python that we'd like to _define_ a new function. We'll need to include it at the beginning of each function definition.
1. Next, we have the name of the function, `foo`. We can name a function using any valid identifier in Python. In general, function names in Python always start with a lowercase letter, and use underscores between the words in the function name if it contains multiple words. 
1. Following the function name, we see a set of parentheses `()` that list the parameters for this function. Since there is nothing included in this example, the function `foo` does not require any parameters.
1. Finally, we see a colon `:` indicating that the indented block of code below this definition is contained within the function. In this case, the function will simply print `Foo` to the terminal.
1. The function ends with the `return` keyword. Since we aren't returning a value, we aren't required to include a `return` keyword in the function. However, it is helpful to know that we may use that keyword to exit the function at any time.

Once that function is created, we can call it using the following code:

```python
foo()
```

### Parameters and Return

{{% youtube imqklu8DFR8 %}}

In a more complex case, we can declare a function that accepts parameters and returns a value, as in this example:

```python
def count_letters(input, letter):
  output = 0
  for i in range(0, len(input)):
    if input[i] == letter:
      output += 1
  return output
```

In this example, the function accepts two parameters: `input`, which could be a string, and `letter`, which could be a single character. However, since Python does not enforce a type on these parameters, they could actually be any value. We could add additional code to this function that checks the type of each parameter and raises a `TypeError` if they are not the expected type.

We can use the parameters just like any other variable in our code. To return a value, we use the `return` keyword, followed by the value or variable containing the value we'd like to return. 

To call a function that requires parameters, we can include values as _arguments_ in the parentheses of the function call:

```python
sum += count_letters("The quick brown fox jumped over the lazy dog", "e")
```
