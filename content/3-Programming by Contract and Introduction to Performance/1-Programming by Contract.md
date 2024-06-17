---
title: "Programming by Contract"
weight: 5
pre: "1. "
---
{{% youtube Ir93pt3KO7c %}}

In this course, we will learn how to develop several different data structures, and then use those data structures in programs that implement several different types of algorithms. However, one of the most difficult parts of programming is clearly explaining what a program should do and how it should perform.

![UML Diagram Example](/images/3/3.1.videouml.png)

So far, we've used UML class diagrams to discuss the structure of a program. It can give us information about the classes, attributes, and methods that our program will contain, as well as the overall relationships between the classes. We can even learn if attributes and methods are private or public, and more.

However, to describe what each method does, we have simply relied on descriptions in plain language up to this point, with no specific format at all. In this module, we'll introduce the concept of _programming by contract_ to help us provide more specific information about what each method should do and the expectations we can count on based on the inputs and outputs of the method.

Specifically, we'll learn about the _preconditions_ that are applied to the parameters of a method to make sure they are valid, the _postconditions_ that the method will guarantee if the preconditions are met, and the _invariants_ that a loop or data structure will maintain. 

Finally, we can put all of that information together to discuss how to prove that an algorithm correctly performs the task it was meant to, and how to make sure that it works correctly in all possible cases. 
