---
title: "Compile & Run Code"
weight: 10
pre: "2. "
---
<!-- Copied from CC 210 -->

{{% youtube x6bEKqhiZHY %}}

Now that we've written our first Java program, we must compile and run the program to see the fruits of our labors. There are many different ways to do this using the Codio platform. We'll discuss each of them in detail here. 

## Terminal

Codio includes a built-in Linux terminal, which allows us to perform actions directly on a command-line interface just like we would on an actual computer running Linux. We can access the Terminal in many ways:

1. Selecting the **Tools** menu, then choosing the **Terminal** option
1. Pressing SHIFT + ALT + T in any Codio window (you can customize this shortcut in your Codio user preferences)
1. Pressing the **Open Terminal** icon in the file tree
1. Selecting the **Open Terminal** option from the **Run** menu (it is the first menu to the right of the **Help** menu)

Additionally, some pages may already open a terminal window for us in the left-hand pane, as this page so helpfully does. As we can see, we're never very far away from a terminal.

{{% notice tip %}}

# New to Linux?

No worries! We'll give you everything you need to know to compile and run your Java programs in this course.

If you'd like to learn a bit more about the Linux terminal and some of the basic commands, feel free to check out this great video on YouTube:

{{% youtube oxuRxtrO2Ag %}}

{{% / notice %}}

Let's go to the terminal window and navigate to our program. When we first open the Terminal window, it should show us a prompt that looks somewhat like this one: 

![Initial Terminal View](/images/1/1.3.j.3.terminal1.png)

There is quite a bit of information there, but we're interested in the last little bit of the last line, where it says `~/workspace`. That is the current directory, or folder, our terminal is looking at, also known as our _working directory_. We can always find the full location of our working directory by typing the `pwd` command, short for "Print Working Directory," in the terminal. Let's try it now!

Enter this command in the terminal:

```bash
pwd
```

and we should see output similar to this:

![pwd Command Output](/images/1/1.3.j.3.pwd.png)

In that output, we'll see that the full path to our working directory is `/home/codio/workspace`. This is the default location for all of our content in Codio, and its where everything shown in the file tree to the far left is stored. When working in Codio, we'll always want to store our work in this directory.

Next, let's use the `ls` command, short for "LiSt," to see a list of all of the items in that directory:

```bash
ls
```

![ls Command Output](/images/1/1.3.j.3.ls.png)

We should see a whole list of items appear in the terminal. Most of them are directories containing examples for the chapters this textbook, including the `HelloWorld.java` file that we edited in the last page. Thankfully, the directories are named in a very logical way, making it easy for us to find what we need. For example, to find the directory for Chapter 1 that contains examples for Java, look for the directory with the name starting with `1j`. In this case, it would be `1j-hello`. 

Finally, we can use the `cd` command, short for "Change Directory," to change the working directory. To change to the `1j-hello` directory, type `cd` into the terminal window, followed by the name of that directory:

```bash
cd 1j-hello
```

![cd Command Output](/images/1/1.3.j.3.cd.png)

We are now in the `1j-hello` directory, as we can see by observing the `~/workspace/1j-hello` on the current line in the terminal. Finally, we can do the `ls` command again to see the files in that directory:

```bash
ls
```

![ls Command Output](/images/1/1.3.j.3.ls2.png)

We should see our `HelloWorld.java` file! If it doesn't appear, try using this command to get to the correct directory: `cd /home/codio/workspace/1j-hello`. 

Once we're at the point where we can see the `HelloWorld.java` file, we can move on to actually compiling and running the program.

## Compiling in Terminal

To compile a Java program in the terminal, we'll use the `javac` command, short for _Java Compiler_, followed by the name of the Java file we'd like to compile. So, in our case, we'll do the following:

```bash
javac HelloWorld.java
```

If it works correctly, we shouldn't get any additional output. The compiler will look through our Java file and create a new file containing the Java bytecode for our program, called `HelloWorld.class`. We can use the `ls` command to see it:

```bash
ls
```

![javac Command Output](/images/1/1.3.j.3.javac.png)

{{% notice info %}}

# Problems?

If the `javac` command gives you any output, or doesn't create a `HelloWorld.class` file, that most likely means that your code has an error in it. Go back to the previous page and double-check that the contents of `HelloWorld.java` exactly match what is shown at the bottom of the page. You can also read the error message output by `javac` to determine what might be going wrong in your file.

We'll cover information about simple debugging steps on the next page as well. If you get stuck, now is a great time to go to **Piazza** and ask for assistance. You aren't in this alone!

{{% / notice %}}

## Running in Terminal

Finally, we can now run our program! Once it is compiled, just type the following in the terminal to run it:

```bash
java HelloWorld
```

![java Command Output](/images/1/1.3.j.3.java.png)

That's all there is to it! We've now successfully compiled and run our first Java program. Of course, we can run the program as many times as we want by repeating the previous `java` command. If we make changes to the `HelloWorld.java` file, we'll need to recompile it using the previous `javac` command first. Then, if those changes instruct the computer to do something different, we should see those changes when we run the program after compiling it. 

{{% notice info %}}

# Try it!

See if you can change the `HelloWorld.java` file to print out a different message. Once you've changed it, use the `javac` and `java` commands to compile and run the updated program. Make sure you see the correct output! 

{{% / notice %}}

## Run Menu

In many of the Codio projects and tutorials in this course, the **Run Menu** will be populated with helpful commands. The **Run Menu** can be found at the top of the screen, right here:

![Run Menu Location](/images/1/1.3.j.3.runmenu.png)

Each Codio project or tutorial may have different items in this menu, since they can be configured by the author of the project. For this book, there will always be the following options:

* Java - Compile File
* Java - Run File

To use these commands, we must simply open up the file we'd like to use, then select the appropriate option from the **Run Menu**. It will automatically use the currently open file in the command. 

So, to compile and run our file, we must simply open `HelloWorld.java` in the panel to the left, then click the arrow in the **Run Menu** and first select **Java - Compile File**. It should open up a Terminal tab and show output similar to the following:

![Compile from Run Menu Output](/images/1/1.3.j.3.runjavac.png)

It looks very similar to the command we entered manually. The only difference is that it uses the folder name along with the filename in the command, which ensures that it gets the correct file without even opening that directory.

Once we've compiled the file, we can go back to that tab and select the **Java - Run File** option. It should show output similar to this:

![Run from Run Menu Output](/images/1/1.3.j.3.runjava.png)

Again, it looks very similar to the commands we performed earlier. Since the Java bytecode file is in a directory, we have to use a `-classpath` option to let Java know where to find the file.

{{% notice info %}}

# Try it!

Make another change to the `HelloWorld.java` file, and then see if you can use the options in the **Run Menu** to compile and run it. Make sure you see the correct output!

{{% / notice %}}

## Codio Assessments

Last, but not least, many of the Codio tutorials and projects in this program will include assessments that we must solve by writing code. Codio can then automatically run the program and check for specific things, such as the correct output, in order to give us a grade. For most of these questions, we'll be able to make changes to our code as many times as we'd like to get the correct answer. Try the example below! 

{Check It!|assessment}(code-output-compare-146573703)

As we can see, there are many different ways to compile and run our code using Codio. Feel free to use any of these methods throughout this course. 
