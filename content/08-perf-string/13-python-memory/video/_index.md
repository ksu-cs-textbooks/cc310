---
title: "Python Character Arrays"
pre: "3.P. "
weight: 31
date: 2019-02-05T10:53:26-05:00
hidden: true
---

{{< youtube gsE16hh3iQQ >}}

#### Resources

* <a href="slides" target="_blank">Slides</a>

#### Video Script

[Slide 1]

In the previous sections, we have talked about why we would need to use strings and how they are a natural choice. When looking into the implementation of strings, we also saw that they could be less than ideal. 

[Slide 2]

We will now talk about how we can have the best of both worlds: utilizing text based data and avoiding repetitive character writes. Some languages, such as Java, have a specific solution for this problem, such as `StringBuilders`. Python does not have class explicitly for this, but we can make our own solution; we can use an array of strings. 

In this context, an array of strings and an array can be nearly interchangeable with only a few modifications. `Arrays` are a mutable sequence of characters whereas `Strings` are an immutable sequence of characters. The `Array` class has built in functions which we can greatly benefit from. 

[Slide 3]

`Arrays` have an `append` function; this allows you to put characters at the end of your `Array`. There is a variety of ways that a coder could implement converting an `Array` to a `String`. One clean and concise way is to use the join function.  This is the main difference between `Strings` and `Arrays`; you will need to use an extra step to get the resulting `String` from an `Array`. 

[Slide 4]

Now that we have the basics of `Arrays`, let's do a memory walk through of the same algorithm from `Strings` but modified to use `Arrays`. This implementation requires the same number of lines; so what's different?

[Slide 5]

I have highlighted the minimal changes that were required. To change to an `Array` implementation, we have only had to change 4 lines: initializing `ENC`, appending to `ENC`, and returning `ENC`. With these changes, we will now see a difference in the number of operations that require new memory allocation as well as character copies!  

[Slide 6]

We will now walk through this example as we did with the `String` implementation. We start with an empty heap and then add the `Array` in the first memory location. Variable `ENC` will be set to point at that location.

[Slide 7-10]

Like before, we start into the loop with the first character, `D`, which maps to `L` after offsetting by `8`. This time when we append `L`, a new memory location is not created. `Arrays` are mutable so their state can change. We proceed to the next iteration of the loop and thus to letter `a`. This maps to `h` after the offset; thus, we append `h`. Again, we do not create a new memory location! We can also note at this point, we have only written the character `L` one time. Continuing on, we go to letter `t` and append the letter `b` to our `Array`. We will now fast forward to the end of the loop and I pose the same questions to you as last time: How many character copies do you think we will make for this `Array`? How many memory entries? Take a moment to pause the video if you would like to determine the pattern for yourself. 

[Slide 11-12]

Skipping ahead to the end of the loop, we have done 14 character copies when encoding the 14 character input string. The number of memory entries is slightly tricky in this context. Precisely at the end of the loop, we have one memory entry. Recall that our return statement was slightly different. Once we get to the return statement here, we need to allocate a new space in memory for the `String` itself. Thus, by the very end of the program, we have used only two memory entries! 

[Slide 13]

Recall that when a `String` was used for our appending, a string with one million characters, had one million one memory addresses filled and five hundred billion five hundred thousand total character copies. Now for an `Array` as our accumulator, a string with one million characters would have one million character copies and only one memory entry! Not taking into account the final conversion as in this case we are just looking at the number of loops. We have a stark improvement! 

Again, modern languages will do periodic clean up so you wouldn't have one million memory locations filled in practice. In the next section, we will discuss a real world comparison and what implications using `Strings` over `Arrays` can have. 
