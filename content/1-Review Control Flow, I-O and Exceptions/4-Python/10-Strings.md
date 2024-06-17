---
title: "Strings"
weight: 50
pre: "10. "
---
{{% youtube ur4m3QjbBHE %}}

Strings are another very important data type in programming. A _string_ is simply a set of characters that represent text in our programs. We can then write programs that use and manipulate strings in a variety of ways, allowing us to easily work with textual data.

## Strings in Flowcharts & Pseudocode

The table below lists the flowchart blocks used to represent strings, as well as the corresponding pseudocode:

| Operation | Flowchart | Pseudocode |
|:---------:|:---------:|:-----------|
| Create String | ![Create String Flowchart Block](/images/1/1.3.x.10.string1.png) | <pre><code>STR = "abc"</code></pre> |
| Access Character | ![Access Character in String Flowchart Block](/images/1/1.3.x.10.string2.png) | <pre><code>C = STR[0]</code></pre> |
| String Length | ![String Length Flowchart Block](/images/1/1.3.x.10.string3.png) | <pre><code>X = size of STR</code></pre> |

## Strings in Python

Let's review the syntax for working with strings in Python.

### String Creation

Strings in Python are declared just like any other variable:

```python
s = "abc123"
```

Notice that strings are enclosed in double quotations marks `"`. Since Python does not have a data type for a single character, we can do the same for single character strings as well:

```python
c = "a"
```

There are several special characters we can include in our strings. Here are a few of the more common ones:
* `\'` - Single Quotation Mark (usually not required)
* `\"` - Double Quotation Mark
* `\n` - New Line
* `\t` - Tab

### String Parsing

{{% youtube 4O-eLkzD50s %}}

Most of the time, we will need to be able to _parse_ strings in order to read input from the user. This is easily done using Python. Let's refer to the skeleton code given in the earlier exercise:

```python
# Load required modules
import sys


def main(argv):

    # If an argument is present, we are reading from a file
    # specified in sys.argv[1]
    if len(argv) > 1:
        reader = open(argv[1])

    # If no argument, read from stdin  
    else:
        reader = sys.stdin

    x = int(reader.readline())

    # -=-=-=-=- MORE CODE GOES HERE -=-=-=-=- 


# main guard
if __name__ == "__main__":
    main(sys.argv)

```

This code will initialize a variable called `reader` to read input from a file if one is provided as a command-line argument. Otherwise, input will be read from the terminal, or `sys.stdin` in Python.

Once we have a reader initialized, we can read a line of data from the input as follows:

```python
line = reader.readline()
```

If we know that line will contain a single item of a different data type, such as an integer, we can also convert that input using the appropriate method:

```python
x = int(reader.readline())
```

Finally, if we have read an entire string of input consisting of multiple parts, we can use the `split` method to split the string in to _tokens_ that are separated by a special _delimiter_. When we do this, we'll have to use special methods to convert the strings to other primitive data types. Here's an example:

```python
line = "This 1 is 2.0 true"
parts = line.split(" ")
first = parts[0]
second = int(parts[1])
third = parts[2]
fourth = float(parts[3])
fifth = bool(parts[4])
```

In this example, we are able to split the first string variable into $5$ parts, each one separated by a space in the original string. Then, we can use methods such as `int()` to convert each individual string token into the desired data type.

### Reading Input in a Loop

When reading an unknown number of lines of input, we can use a loop in Python such as the following example:

```python
for line in reader:
    line = line.strip()
    if not line or len(line) == 0:
        break
    
    # parse the input
```

This will read input until either a blank line is received (usually via the terminal), or there is no more input available to read (from a file). 

### String Operations

There are also several operations we can perform on strings in Python:

```python
s1 = "This"
s2 = "That"

# string length
x = len(s1)

# string comparison
# can use standard comparison operators
b1 = s1 == s2
b2 = s1 < s2 

# concatenation
s3 = s1 + " " + s2
```

Additional methods can be found on the [Python Built-In Types: str](https://docs.python.org/3/library/stdtypes.html#text-sequence-type-str) and
[Python Common String Operations](https://docs.python.org/3/library/string.html) pages

### String Formatting

Strings can also be used to create formatted output in Python through the use of the `format()` method. Here's a short example:

```python
sum = 123
avg = 1.23
name = "Student"

output = "{}: Your score is {} with an average of {}."

print(output.format(name, sum, avg))
```

When we run this program, the output will be:

```tex
Student: Your score is 123 with an average of 1.23.
```

Each item in the formatted output can also be given additional attributes such as _width_ and _precision_. More details can be found on the [Python Format String Syntax](https://docs.python.org/3/library/string.html#format-string-syntax) page.

## References

* [Python Built-In Types: str](https://docs.python.org/3/library/stdtypes.html#text-sequence-type-str)
* [Python Common String Operations](https://docs.python.org/3/library/string.html)
* [Python Format String Syntax](https://docs.python.org/3/library/string.html#format-string-syntax)
