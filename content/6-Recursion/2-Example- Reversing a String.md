---
title: "Example: Reversing a String"
weight: 10
pre: "2. "
---
Suppose we must write a program that reads in a sequence of keyboard characters and prints them in reverse order. The user ends the sequence by typing an asterisk character `*`.

We could solve this problem using an array, but since we do not know how many characters might be entered before the `*`, we could not be sure the program would actually work. However, we can use a recursive function since its ability to save the input data is not limited by a predefined array size. 

Our solution would look something like this. We've also numbered the lines to make the following discussion easier to understand.

```tex
function REVERSE()			    (1)
    read CHARACTER			    (2)
    if CHARACTER == `*` then	(3)
        return			        (4)
    else				        (5)
        REVERSE()			    (6)
        print CHARACTER		    (7)
        return			        (8)
    end if 				        (9)
end function				    (10)
```

## Base Case

The function first reads a single character from the keyboard and stores it in `CHARACTER`. Then, in line 3 it checks to see if the user typed the `*` character. If so, we simply return, knowing that we have reached the end of the input and need to start printing out the characters we've read in reverse order. This is the _base case_ for this recursive function.

## Recursive Case

If the `CHARACTER` we read in was not an `*`, line 6 will recursively call `REVERSE` to continue reading characters. Once the function returns (meaning that we have gotten an `*` character and started the return process) the function prints the `CHARACTER` in line 7 and then returns itself.

## Behind the Scenes

Now let's look at what happens within the computer when we run `REVERSE`. Let's say the program user wants to enter the three characters from the keyboard: `n`, `o`, and `w` followed by the `*` character. The following figure illustrates the basic concept of what is going on in the computer. 

![Reverse Head Recursive Activation Stack](/images/6/6.2.reverse-head.png)
 
The arrows in the figure represent the order of execution of the statements in the computer. Each time we execute the recursive call to `REVERSE` in line 6, we create a new instance of the function, which starts its execution back at the beginning of the function (line 2). Then, when the function executes `return`, control reverts back to the next statement to be executed (line 7) in the calling instance of the function. 

It's important to understand that each instance of the function has its own set of variables whose values are unique to that instance. When we read `n` into the `CHARACTER` variable in the first instance of `REVERSE` it is not affected by anything that happens in the second instance of `REVERSE`.  Therefore, reading the `o` into `CHARACTER` in the second instance of `REVERSE` does not affect the value of `CHARACTER` in the first instance of `REVERSE`.

During the execution of the first instance of `REVERSE`, the user enters the character `n` so the `if` condition is `false` and we execute the `else` part of the statement, which calls the `REVERSE` function. (Note that before we actually start the second instance of `REVERSE`, the operating system stores the statement where we will pick up execution once the called function returns.) When the second instance of `REVERSE` is started, a new copy of all variables is created as well to ensure we do not overwrite the values from the first instance.

The execution of the second instance of  `REVERSE` runs exactly like the first instance except that the user enters the character `o` instead of `n`. Again, the `else` part of the `if` statement is executed, which calls the `REVERSE` function. When the third instance of `REVERSE` is executed, the user now inputs `w`, which again causes a new instance of `REVERSE` to be called. 

Finally, in the fourth instance of `REVERSE`, the user inputs the `*` character, which causes the `if` part of the statement to execute, which performs our `return` statement. Once the `return` from the base case of our recursive function is performed, it starts the process of ending all the instances of the `REVERSE` function and creating the solution. When instance 4 of the `REVERSE` function returns, execution starts at the `write` statement (line 7) of instance 3. Here the character `w` is printed, and the function returns to instance 2. The same process is carried out in instance 2, which prints the `o` character and returns. Likewise, instance 1 prints its character `n` and then returns. The screen should now show the full output of the original call to `REVERSE` , which is "won".

Recursion has allowed us to create a very simple and elegant solution to the problem of reversing an arbitrary number of characters. While you can do this in a non-recursive way using loops, the solution is not that simple. If you don't believe us, just try it! (Yes, that is a challenge.)
