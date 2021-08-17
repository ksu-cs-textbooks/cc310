---
title: "Syntax Overview"
weight: 5
pre: "1. "
---
Let's discuss some of the basic concepts we need to understand about the Python programming language.

## Program Structure

To begin, let's look at a simple Hello World program written in Python:

```python
def main():
    print("Hello World!")


# main guard
if __name__ == "__main__":
    main()

```

This program contains multiple important parts:

1. First, we define a function called `main()`. Python does not require us to do this, since we can write our code directly in the file and it will execute. However, since we are going to be building larger programs in this course, it is a good idea to start using functions now. 
1. The function definition ends with a colon `:`, and then the code inside of that function comes directly after it. The code contained in the function must be indented a single level. By convention, Python files should use 4 spaces to indent the code. Thankfully, Codio does that for us automatically.
1. At the bottom of the file, we've included a **main guard** that determines if this file is being executed. If it is, it will call the `main()` function to run the program. 

Of course, this is a very brief overview for the Python programming language. To learn more, feel free to refer to the references listed below, as well as the textbook content for previous courses. 

{{% notice info %}}

# Try It!

See if you can use the code above to write your own Hello World program in the `HelloWorld.py` file that is open to the left. We'll learn how to compile and run that program on the next page. 

{{% / notice %}}

## References

* [The Python Tutorial](https://docs.python.org/3/tutorial/) from Python
* [Python Tutorial](https://www.w3schools.com/python/) from W3Schools
* [Python Tutorial](https://www.tutorialspoint.com/python/index.htm) from Tutorials Point
