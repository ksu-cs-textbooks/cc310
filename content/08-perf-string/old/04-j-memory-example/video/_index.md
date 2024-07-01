---
title: "StringBuilders"
pre: "3.J. "
weight: 30
date: 2019-02-05T10:53:26-05:00
hidden: true
---

{{< youtube mHOqqh-M2us >}}

#### Resources

* <a href="slides" target="_blank">Slides</a>
* [StringBuilders](https://docs.oracle.com/javase/7/docs/api/java/lang/StringBuilder.html)

#### Video Script
[Slide 1]

In the previous sections, we have talked about why we would need to use strings and how they are a natural choice. When looking into the implementation of strings, we also saw that they could be less than ideal. 

[Slide 2]

We will now talk about how we can have the best of both worlds: utilizing text based data and avoiding repetitive character writes. Java has a specific class for this problem: `StringBuilders`.

`StringBuilders` and `Strings` can be nearly interchangeable with only a few modifications. `StringBuilders` are a mutable sequence of characters whereas `Strings` are an immutable sequence of characters. The `StringBuilder` class has built in functions which we can greatly benefit from. First, lets discuss initialization; upon initializing a `StringBuilder` will have no characters and an initial capacity of 16 characters and will be automatically made larger if needed. You can also specify a capacity upon initialization if you would like. 

[Slide 3]

You can read more about `StringBuilders` in the Java documentation and we will cover some of the methods you will most likely utilize. `StringBuilders` have an `append` function; this allows you to put characters at the end of your `StringBuilder`. `StringBuilders`, like many other classes, also have a `toString()` function. This is the main difference between `Strings` and `StringBuilders`; you will need to use an extra step to get the resulting `String` from a `StringBuilder`. 

[Slide 4]

Now that we have the basics of `StringBuilders`, let's do a memory walk through of the same algorithm from `Strings` but modified to use `StringBuilders`. This implementation requires the same number of lines; so what's different?

[Slide 5]

I have highlighted the minimal changes that were required. To change to a `StringBuilder` implementation, we have only had to change 4 lines: initializing `ENC`, appending to `ENC`, and returning `ENC`. With these changes, we will now see a difference in the number of operations that require new memory allocation as well as character copies!  

[Slide 6]

We will now walk through this example as we did with the `String` implementation. We start with an empty heap and then add the `StringBuilder` in the first memory location. Variable `ENC` will be set to point at that location. For this implementation, the simplest way to visualize the `StringBuilder` is in the form of a character array. It is important to note that an array of characters and a `StringBuilder` are distinctly different in code. 

[Slide 7-10]

Like before, we start into the loop with the first character, `D`, which maps to `L` after offsetting by `8`. This time when we append `L`, a new memory location is not created. `StringBuilders` are mutable so their state can change. We proceed to the next iteration of the loop and thus to letter `a`. This maps to `h` after the offset; thus, we append `h`. Again, we do not create a new memory location! We can also note at this point, we have only written the character `L` one time. Continuing on, we go to letter `t` and append the letter `b` to our `StringBuilder`. We will now fast forward to the end of the loop and I pose the same questions to you as last time: How many character copies do you think we will make for this `StringBuilder`? How many memory entries? Take a moment to pause the video if you would like to determine the pattern for yourself. 

[Slide 11-12]

Skipping ahead to the end of the loop, we have done 14 character copies when encoding the 14 character input string. The number of memory entries is slightly tricky in this context. Precisely at the end of the loop, we have one memory entry. Recall that our return statement was slightly different. Once we get to the return statement here, we need to allocate a new space in memory for the `String` itself. Thus, by the very end of the program, we have used only two memory entries! 

[Slide 13]

Recall that when a `String` was used for our appending, a string with one million characters, had one million one memory addresses filled and five hundred billion five hundred thousand total character copies. Now for a `StringBuilder` as our accumulator, a string with one million characters would have one million character copies and only one memory entry! Not taking into account the final conversion as in this case we are just looking at the number of loops. We have a stark improvement! 

Again, modern languages will do periodic clean up so you wouldn't have one million memory locations filled in practice. In the next section, we will discuss a real world comparison and what implications using `Strings` over `StringBuilders` can have. 
