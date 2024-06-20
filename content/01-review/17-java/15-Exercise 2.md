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

{Check It!|assessment}(test-2449394732)

{{% notice info %}}

# Solution

```java
import java.util.Scanner;
import java.nio.file.Files;
import java.nio.file.Paths;
import java.nio.file.InvalidPathException;
import java.nio.file.NoSuchFileException;
import java.io.BufferedWriter;
import java.io.IOException;
import java.lang.NumberFormatException;

public class Exercise2{
    public static void main(String[] args){
        if(args.length != 3){
            System.out.println("Invalid Arguments");
            return;
        }

        try(
            Scanner scanner1 = new Scanner(Paths.get(args[0]));
            Scanner scanner2 = new Scanner(Paths.get(args[1]));
            BufferedWriter writer = Files.newBufferedWriter(Paths.get(args[2]))
        ){

            int countPos = 0;
            int countNeg = 0;
            double sumPos = 0;
            double sumNeg = 0;

            while(scanner1.hasNext()){
                String line = scanner1.nextLine().trim();
                double input = Double.parseDouble(line);
                if(input >= 0){
                    countPos += 1;
                    sumPos += input;
                }else{
                    countNeg += 1;
                    sumNeg += input;
                }
            }

            while(scanner2.hasNext()){
                String line = scanner2.nextLine().trim();
                double input = Double.parseDouble(line);
                if(input >= 0){
                    countPos += 1;
                    sumPos += input;
                }else{
                    countNeg += 1;
                    sumNeg += input;
                }
            }

            writer.write("" + countPos);
            writer.newLine();
            writer.write("" + sumPos);
            writer.newLine();
            writer.write("" + countNeg);
            writer.newLine();
            writer.write("" + sumNeg);
            writer.newLine();
            System.out.println("Complete");

        }catch(InvalidPathException e){
            System.out.println("Invalid Arguments");
            return;
        }catch(NoSuchFileException e){
            System.out.println("Invalid Arguments");
            return;
        }catch(IOException e){
            System.out.println("Invalid Arguments");
            return;
        }catch(NumberFormatException e){
            System.out.println("Invalid Input");
            return;
        }
    }
}
```

{{% / notice %}}
