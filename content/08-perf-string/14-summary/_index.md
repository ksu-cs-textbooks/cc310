---
title: "Summary"
weight: 70
pre: "14. "
---

In this module, we reviewed each of the data structures we have explored in this class. Most importantly, we looked at how they compare in terms of performance and discussed some of the best and most efficient ways to use them in our programs. 

Using that information, we introduced the standard collection libraries for both Java and Python, and saw how those professional implementations closely follow the same ideas and analysis that we saw in our own structures. While the professional structures may have many more features and more complex code, at the core they still work just like the structures we learned how to build from scratch.

One of the best traits of a good programmer is knowing how to most effectively use the tools made available to us through the programming languages and libraries we have chosen to use. The goal of this class is to give us the background we need to understand how the various collection data structures we can choose from work, so that we can use them in the most effective way to build useful and efficient programs. 

{{< youtube MJ1tkFIDEAA  >}}

[Video Materials](video)

To start this course, we have looked into strings. They are a very natural way to represent data, especially in real world applications. Often though, the datapoints can be very large and require multiple modifications. We also examined how strings work: element access, retrieving the size, and modifying them. We looked into some alternatives which included StringBuilders for Java and character arrays for Python.

To really understand this point, we have included a comparison. We have implemented the APPENDER and APPENDER_LIST functions in both Python and Java. For the Java implementation, we utilized StringBuilders.

 ```tex
 1. function APPENDER(NUMBER, BASE)
 2.     RESULT = ""
 3.     loop I from 1 to NUMBER
 4.         RESULT = RESULT + BASE
 5.         if I MOD 2 = 0
 6.             RESULT = RESULT + " "
 7.         else
 8.             RESULT = RESULT + ", " 
 9.     end loop
 10.    return RESULT
 11. end function
 ```

 ```tex
 1. function APPENDER_LIST(NUMBER, BASE)
 2.     RESULT = []
 3.     loop I from 1 to NUMBER
 4.         RESULT.APPEND(BASE) 
 5.         if I MOD 2 = 0
 6.             RESULT.APPEND(" ") 
 7.         else
 8.             RESULT.APPEND(", ")  
 9.     end loop
 10.    RESULT = "".JOIN(RESULT)
 11.    return RESULT
 12. end function
 ```

{{% notice info %}}

For the tests of 10<sup>8</sup> and 10<sup>9</sup> in Java, the string implementation took over 24 hours and the StringBuilder implementation ran out of memory. For these reasons, they are omitted from the figure. 
 
{{% / notice %}}

![Python Time](/images/13/315_stringsTime_python.png)
![Java Time](/images/13/315_stringsTime_java.png)

These figures compare Strings and lists for Python and Strings and StringBuilders for Java. The intention of these is not to compare Python and Java. 

In both languages, we see that the string function and the respective alternative performed comparably until approximately 10<sup>6</sup> (1,000,000 characters). Again, these are somewhat contrived examples with the intention of understanding side effects of using strings. 

As we have discussed, modern coding languages will have clean up protocols and memory management strategies. With the intention of this class in mind, we will not discuss the memory analysis in practice. 

When modifying strings we need to be cognizant of how often we will be making changes and how large those changes will be. If we are just accessing particular elements or only doing a few modifications then using plain strings is a reasonable solution. However, if we are looking to build our own DNA sequence this is not a good way to go as strings are immutable.


