---
title: "Exceptions"
weight: 65
pre: "12. "
---

{{< youtube Tp9jbKRVqQI  >}}

An _exception_ is an error that a program encounters when it is running. While some errors cannot be dealt with directly by the program, many of these exceptions can be _caught_ and _handled_ directly in our programs. 

## Exceptions in Flowcharts & Pseudocode

There isn't really a standard way to display exceptions in flowcharts and pseudocode, but we can easily create a system that works well for our needs. Below are the flowchart blocks and pseudocode examples we'll use in this course to represent exceptions and exception handling:

| Operation | Flowchart | Pseudocode |
|:---------:|:---------:|:-----------|
| Throw Exception | ![Throw Exception Flowchart Block](/images/1/1.3.x.11.exception1.png) | <pre><code>throw INPUT EXCEPTION</code></pre> |
| Catch Exception | ![Catch Exception in String Flowchart Block](/images/1/1.3.x.11.exception2.png) | <pre><code>catch INPUT EXCEPTION</code></pre> |
| Try-Catch Example | ![Try-Catch Example Flowchart Blocks](/images/1/1.3.x.11.exception3.png) | <pre><code>X = 0<br>try<br>    input X<br>    if X &lt; 0<br>        throw INPUT EXCEPTION<br>    end if<br>    print X<br>catch INPUT EXCEPTION<br>    print "Error"<br>end try</code></pre> |

## Exceptions in Python

Let's review the syntax for working with exceptions in Python.

### Try-Catch

In Python, we can use a **Try-Except** statement to detect and handle exceptions in our code:

```python
# Load required modules
import sys

try:
    reader = open(sys.argv[1])
    x = int(reader.readline())
    print(x)

except Exception as e:
    print("Error!")

```

In this example, the program will try to open a file using the first command-line argument as a file name. There are several exceptions that could occur in this code, such as a `ValueError`, a `IndexError`, a `FileNotFoundError`, and more. They can also be handled individually:

```python
# Load required modules
import sys

try:
    reader = open(sys.argv[1])
    x = int(reader.readline())
    print(x)

except IndexError as e:
    print("Error: Invalid Array Index!")
except FileNotFoundError as e:
    print("Error: File Not Found!")
except ValueError as e:
    print("Error: Input Does Not Match Expected Format!")
except OSError as e:
    print("Error: OS Exception!")
```

### Throw

If desired, we can also _raise_ our own exceptions in Python:

```python
if y == 0:
    raise ValueError("Cannot divide by zero")
else:
    z = x / y
    print(z)
```

This will cause an exception to be thrown if the value of `y` is equal to $0.0$. 

### Finally

We can also add **Else** and **Finally** blocks at the end of each **Try-Except** block.  A **Finally** block will be executed whenever the control exits the **Try-Except** block, even through the use of a `return` statement to return from a method. The **Else** block will be executed if the entire **Try-Except** block completes without any exceptions being raised:

```python
# Load required modules
import sys

try:
    reader = open(sys.argv[1])
    x = int(reader.readline())
    print(x)

except Exception as e:
    print("Error!")
else:
    print("No Errors!")
finally:
    print("Finally Block")

```

### With Statement

When working with resources such as files in Python, we can also use a **With** block to ensure that those resources are properly closed when we are done with them. In addition, a **With** block will automatically catch and suppress any exceptions that result from trying to close the resource after an exception has occurred, preventing us from being bombarded by unavoidable exceptions. Here's an example:

```python
import sys

try:    
    with open(sys.argv[1]) as reader:
        x = int(reader.readline())
        print(x)

except IndexError as e:
    print("Error: Invalid Array Index!")
except ValueError as e:
    print("ValueError: {}".format(e))
except FileNotFoundError as e:
    print("FileNotFoundError: {}".format(e))
```

In this example, we are opening a file using the `open()` method inside of the **With** statement. That file will automatically be closed once the program leaves the **With** statement. 

## References

* [Built-in Exceptions](https://docs.python.org/3/library/exceptions.html)
* [Tutorial: Errors and Exceptions](https://docs.python.org/3/tutorial/errors.html)
* [Python Exception Hierarchy](https://docs.python.org/3/library/exceptions.html#exception-hierarchy)
