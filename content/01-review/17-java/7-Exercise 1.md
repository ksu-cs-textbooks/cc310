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

```java
// Load required classes
import java.util.Scanner;
import java.io.File;

public class Exercise1{
  
    public static void main(String[] args) throws Exception{

        // Scanner variable
        Scanner reader;

        // If an argument is present, we are reading from a file
        // specified in args[0]
        if(args.length > 0){
          reader = new Scanner(new File(args[0]));

        // If no argument, read from System.in
        }else{
          reader = new Scanner(System.in);
        }

        // read a single integer from input
        int x = reader.nextInt();

        /* -=-=-=-=- MORE CODE GOES HERE -=-=-=-=- */

    }
}
```

This code will create a `Scanner` variable called `reader`, and initialize it to either read from file provided as a command-line argument, or from the terminal if an argument is not provided. It will then read a single integer from the input, storing it in the variable `x`.

To complete this exercise, we can continue to write this program where the `MORE CODE GOES HERE` comment is in the skeleton code.

{Check It!|assessment}(code-output-compare-4282752777)

{{% notice info %}}

# Solution

```java
// Load required classes
import java.util.Scanner;
import java.io.File;

public class Exercise1{
  
    public static void main(String[] args) throws Exception{

        // Scanner variable
        Scanner reader;

        // If an argument is present, we are reading from a file
        // specified in args[0]
        if(args.length > 0){
          reader = new Scanner(new File(args[0]));

        // If no argument, read from System.in
        }else{
          reader = new Scanner(System.in);
        }

        // read a single integer from input
        int x = reader.nextInt();

        int sum = 0;
        for(int i = 1; i <= x; i++){
            if(i % 3 != 0){
                sum += i;
            }
        }
        System.out.println(sum);

    }
}
```
{{% / notice %}}
