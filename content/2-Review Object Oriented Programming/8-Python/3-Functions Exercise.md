---
title: "Functions Exercise"
weight: 15
pre: "3. "
---
Before we learn about classes and objects, let's do a quick exercise to review how to create and use functions in our code.

## Problem Statement

> Write a program that accepts input from a file provided as a command-line argument. If an incorrect number of arguments are provided, or if the program is unable to open the file, it should print "Invalid Arguments" and terminate. 

> The program's input will consist of a list of 100 integers, one per line. If any line of the input cannot be converted to an integer, the program should print "Invalid Input" and terminate.

> The program should determine whether the list of integers is considered a _mathematical set_. That is, each item in the list should be unique, with no duplicate numbers. If the input is not a set, it should print "Not a set" and terminate.

> If the input is a set, then the program should print the sum of the values in the set and then terminate.  

> This program should consist of three functions:

> * `main(args)` - The main function that controls the program. It should accept an array of strings representing the command-line arguments to the program.
> * `is_set(numbers)` - A function to determine if the given array is a set. The input should be a single array of integers, and the return value should be a Boolean value.
> * `sum_set(numbers)` - A function to find the sum of all the elements in the given array. The input should be a single array of integers, and the return value should be an integer. 

Don't forget to include a main guard at the end of the file that passes the contents of `sys.argv` as an argument to the `main()` function. 

{{% notice info %}}

# Finding a Set

There may be easier ways of determining if an array contains duplicate items, but could we simply check that, for each item, there is only one of that item in the list? 

{{% / notice %}}

## Grading

This exercise uses a custom grading program to grade submissions, which will be used extensively throughout this course. The first step of the grading process will examine the structure of your code, making sure that it contains the correct classes and functions. The second step will directly examine each function in the program, making sure that they operate as expected. You are welcome to include any additional code to complete the project that is not specified above. 

Each step of the grading process will create two files in your work directory showing more detailed output. To open the HTML file as a webpage, right-click on it and select **Preview Static**.  The log file may contain helpful debugging messages if your program experiences an unhandled exception. 

{Check It!|assessment}(test-4065492757)

{Check It!|assessment}(test-2578058679)

{{% notice info %}}

# Solution

```python
import sys


def main(argv):

    if len(argv) != 2:
        print("Invalid Arguments")
        sys.exit()

    try:
        with open(argv[1]) as scanner1:

            nums = []
            for line in scanner1:
                line = line.strip()
                input = int(line)
                nums.append(input)

            if is_set(nums):
                print(sum_set(nums))
            else:
                print("Not a set")

    except FileNotFoundError:
        print("Invalid Arguments")
        return
    except IOError:
        print("Invalid Arguments")
        return
    except ValueError:
        print("Invalid Input")
        return


def is_set(nums):
    for i in nums:
        count = 0
        for j in nums:
            if i == j:
                count += 1
        if count > 1:
            return False
    return True


def sum_set(nums):
    sum = 0
    for i in nums:
        sum += i
    return sum


# main guard
if __name__ == "__main__":
    main(sys.argv)

```

{{% / notice %}}
