---
title: "Immutable"
pre: "2. "
weight: 20
date: 2019-02-04T10:53:26-05:00
hidden: true
---

{{< youtube KII6o4G5I_U >}}

#### Resources

* <a href="slides" target="_blank">Slides</a>

#### Video Script
[Slide 1]

In this video we will discuss what is going on behind the scenes when we utilize strings. 

[Slide 2]

A String is a structure that contains an ordered set of characters. Characters can be letters, numbers, symbols, and whitespace. Strings can contain any number and combination of characters. Thus, strings could be single characters, words, sentences, and even literal books! 

[Slide 3]

I will take a moment to explain the notation that we will be using in this course to work with strings. We will have two boxes, one labeled Heap and one labeled Variable (or Variables if there are multiple that we want to keep track of). The current value of the variable will be shown in the Variable box. The heap box has memory locations and potentially values in those. For example, we use `0x1` to denote the first spot in memory, `0x2` to denote the second and so on. By using the `0x` prefix, we are making explicitly clear that we are referring to a memory location. 

[Slide 4]

Recall that strings are reference variables. This means that the variable contains the memory address of the value. In this instance, we may have set the string called `RESULT` equal to `"Go Cats!"`, the value that is actually contained in `RESULT` will be a pointer to the memory location for the string `"Go Cats!"`. This principle is why we look at the heap and variable values when walking through while memory mapping. 

[Slide 5]

Working with strings presents some unintended consequences. Strings are an immutable data type which means that once declared their state cannot change. We will now look at an example of where this can cause trouble in our coding.

Here we have a basic function, called `ENCODER`. As input, it takes `TEXT` which is the text to encode and `X` which is a number for the offset. This is a very basic encoding strategy where we essentially shift the letters. This is not a good encoding strategy as it is very weak. 

[Slide 6]

For example lets say we have a string `"Fish"` which we want to encode by offsetting 2. `F` becomes `H`, `i` becomes `k`, `s` becomes `u`, and `h` becomes `j`. This is a very natural implementation of a task such as encoding and on the surface does not appear to be a bad practice. However, we will see that this implementation is not ideal. Let's walk through an example. 

[Slide 7]

Let's say we call the `ENCODER` function with the string `"Data is great!"` and an offset of `8`. For the purposes of the example, we will start with an empty heap. 

[Slides 8-13]

We begin by initializing the variable `ENC` to an empty string, creating a new entry in memory and assigning `ENC` to the first spot in memory. 
We then start our loop and the first character is `D`. When offset by `8`, this gives us `L`.
We append `L` to `ENC`. Since strings are immutable, meaning their state cannot change, this creates a new place in memory for the string that contains `L`. Our variable is updated to point to the second memory spot. 

[Slides 14-16]

We move on to the second iteration: character `a` which is offset to `h`. 
We then append `h` to `ENC`. Again, this creates a new string in memory and updates `ENC` to point to the third memory location. It is also important to note that the character `L` has been written twice now. Making a total of `3` character writes for a two character string in this example. 

[Slides 17-20]

Now to the third iteration of the loop which is `t`, and the offset character will be the character `b`. As before, we have a new memory entry and update the pointer for `ENC`. Now we have done a total of `6` character copies for a three character string! We continue our loop in this fashion. We will now fast forward to the end of the loop. How many character copies do you think we will make for this string? How many memory entries? Take a moment to pause the video if you would like to determine the pattern for yourself. 

[Slide 21]

Skipping ahead, we see that there have been `15` memory entries for a `14` character string. Doing some math, there are `105` character copies for the string! In terms of computational time, this will add up! 

[Slide 22]

I have outlined here how many character copies have occurred and how many memory locations have been created. 

[Slide 23-24]

We can generalize this to the following. You don't need to worry about determining these equations! I calculated them to show you the gravity of using plain strings. While it doesn't seem cumbersome for smaller strings and thus fewer iterations, it really adds up. 
For a string with one million characters, that would be one million one memory addresses filled and five hundred billion five hundred thousand total character copies. While modern coding languages will do periodic clean up routines and try to optimize this behavior, we need to be mindful of the way we implement strings. Even though it seems bleak, there is an alternative that we will discuss in the next section that offers considerable improvements. 
