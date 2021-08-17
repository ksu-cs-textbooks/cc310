---
title: "Exercise 1"
weight: 35
pre: "7. "
---
At this point, we've covered enough material to build a simple program. So, let's see if we can complete the following example program before continuing. 

## Problem Statement

> Write a program that reads an integer from either the terminal, or a file if one is provided as a command-line argument. It should not worry about handling any exceptions encountered.

> The program should compute and print the sum of all integers from 1 up to and including the integer provided as input, except those integers which are evenly divisible by 3. If the provided input is not a positive integer, the program should simply print 0.

## Skeleton Code

Since we haven't covered how to handle input yet, we can use the following skeleton code to help us build our program.

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

This code will create a `Scanner` variable called `reader`, and initialize it to either read from file provided as a command-line argument, or from the terminal if an argument is not provided. It will then read a single integer from the input, storing it in the variable `x`.

To complete this exercise, we can continue to write this program where the `MORE CODE GOES HERE` comment is in the skeleton code.

{Check It!|assessment}(code-output-compare-2708968079)

{{% notice info %}}

# Solution

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

    sum = 0

    for i in range(1, x + 1):
        if i % 3 != 0:
            sum += i

    print(sum)


# main guard
if __name__ == "__main__":
    main(sys.argv)

```

{{% / notice %}}
