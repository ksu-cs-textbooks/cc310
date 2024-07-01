---
title: "Memory Analysis"
pre: "5. "
weight: 61
date: 2019-02-05T10:53:26-05:00
hidden: true
---

{{< youtube MJ1tkFIDEAA >}}

#### Resources

* <a href="slides" target="_blank">Slides</a>


#### Video Script

[Slide 1]

We have discussed strings in a very theoretic way up to this point. Now we hope to shed light on strings in practice. 

[Slide 2]

Throughout this module, we have discussed why we would want to use strings as a data structure, how they are used behind the scenes, and how we can improve upon that performance. For Java, we looked at `StringBuilders` and for Python, we looked at `Arrays`. Regardless of the language and the replacement of the `String`, we saw dramatic improvements on the number of character copies as well as memory entries. 

[Slide 3]

I have taken the pseudoscode from each example and implemented them in both languages. 

[Slide 4]

Here we can see a comparison in each language of strings versus the languages alternative. This is not intended to draw comparisons on performance between the languages themselves. We are comparing performance in terms of time in these figures. For both languages, we see that Strings and the alternatives perform somewhat similarly until about one million characters. After that point, we see a stark difference between the string methods and their alternatives. For on the tests of 10<sup>8</sup> and 10<sup>9</sup> in Java, the string implementation took over 24 hours and the StringBuilder implementation ran out of memory. For these reasons, they are omitted from the figure. 

[Slide 5]

In the context of this course, there are too many factors to take into consideration to do a fair memory analysis. We feel that this is beyond the scope of the module. However, we can offer a brief discussion of why memory analysis is not cut and dry. Many languages use what computer scientists refer to as garbage collection. The language will periodically clear out memory while running if it determines the memory is not necessary. In this application of strings, some languages have built in modifications of strings to better handle the immutability of strings. So you may be asking yourself: where does that leave us? 

[Slide 6]

Should we use strings or find an alternative? There is not a hard and fast rule that determines which cases are better suited for alternatives. A general rule of thumb is that strings are not terrible. Any time that you are making a lot of modifications to strings, such as appending characters, you may want to consider the alternative for the particular language. There is no defined number of 'a lot of modifications'. As we saw in the time comparisons, for the most part, run time was similar but after a certain number of iterations it was clear that there was a performance difference. Strings will continue to be used in many applications and the best that we can do is be cognizant of the potential drawbacks and what alternatives exist. 
