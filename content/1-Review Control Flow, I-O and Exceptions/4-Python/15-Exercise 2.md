---
title: "Exercise 2"
weight: 75
pre: "15. "
---
Let's build another sample program to review the content we've covered thus far.

## Problem Statement

> Write a program that accepts three files as command line arguments. The first two represent input files, and the third one represents the desired output file. If there aren't three arguments provided, either input file is not an existing file, or the output file is an existing directory, print "Invalid Arguments" and exit the program. The output file may be an existing file, since it will be overwritten. 

> The program should open each input file and read the contents. Each input file will consist of a list of numbers, one per line. The numbers may be integers or floating point numbers. If there are any errors parsing the contents of either file, the program should print "Invalid Input" and exit. As the input is read, the program should keep track of both the count and sum of all positive and negative inputs. 

> Once all input is read, the program should open the output file and print the following four items, in this order, one per line: number of positive inputs, sum of positive inputs, number of negative inputs, sum of negative inputs.

> Finally, when the program is done, it should simply print "Complete" to the terminal and exit. Don't forget to close any open files! Your program must catch and handle all possible exceptions, printing either "Invalid Arguments" or "Invalid Input" as described above.

We can use any of the code examples on previous pages to help us complete this exercise. 

This exercise uses a custom grading program to grade submissions, which will be used extensively throughout this course. The grading program will create two files in your work directory showing more detailed output. To open the HTML file as a webpage, right-click on it and select **Preview Static**.  The log file may contain helpful debugging messages if your program experiences an unhandled exception.

{Check It!|assessment}(test-3534615650)

{{% notice info %}}

# Solution

```python
import sys


def main(argv):

    if len(argv) != 4:
        print("Invalid Arguments")
        sys.exit()

    try:
        with open(argv[1]) as scanner1, open(argv[2]) as scanner2, \
                open(argv[3], "w") as writer:

            countPos = 0
            countNeg = 0
            sumPos = 0
            sumNeg = 0

            for line in scanner1:
                line = line.strip()
                input = float(line)
                if input >= 0:
                    countPos += 1
                    sumPos += input
                else:
                    countNeg += 1
                    sumNeg += input

            for line in scanner2:
                line = line.strip()
                input = float(line)
                if input >= 0:
                    countPos += 1
                    sumPos += input
                else:
                    countNeg += 1
                    sumNeg += input

            writer.write("{}\n".format(countPos))
            writer.write("{}\n".format(sumPos))
            writer.write("{}\n".format(countNeg))
            writer.write("{}\n".format(sumNeg))

            print("Complete")

    except FileNotFoundError as e:
        print("Invalid Arguments")
        return
    except IOError as e:
        print("Invalid Arguments")
        return
    except ValueError as e:
        print("Invalid Input")
        return


# main guard
if __name__ == "__main__":
    main(sys.argv)

```

{{% / notice %}}
