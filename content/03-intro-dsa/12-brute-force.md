---
title: "Brute Force"
weight: 60
pre: "12. "
disableMathJax: false
---

The first algorithmic technique we'll use is the _brute force_ technique. This is the algorithmic technique that most of us are most familiar with, even if we don't realize it. 

Simply put, a brute force algorithm will try all possible solutions to the problem, only stopping when it finds one that is the actual solution. A great example of a brute force algorithm in action is plugging in a USB cable. Many times, we will try one way, and if that doesn't work, flip it over and try the other. Likewise, if we have a large number of keys but are unsure which one fits in a particular lock, we can just try each key until one works. That's the essence of the brute force approach to algorithmic design.

## Example - Closest Pair

![Closest Pair of Points](/images/4/4.13.pair.png)[^1]

[^1]: File:Closest pair of points.svg. (2018, October 20). Wikimedia Commons, the free media repository. Retrieved 22:29, February 8, 2020 from https://commons.wikimedia.org/w/index.php?title=File:Closest_pair_of_points.svg&oldid=324759130.

A great example of a brute force algorithm is finding the closest pair of points in a multidimensional space. This could be as simple as finding the two closest cities on a map, or the two closest stars in a galaxy.

To find the answer, a brute force approach would be to simply calculate the distance between each individual pair of points, and then keep track of the minimum distance found. A pseudocode version of this algorithm would be similar to the following.

```tex
MINIMUM = infinity
POINT1 = none
POINT2 = none
loop each POINTA in POINTS
    loop each POINTB in POINTS
        if POINTA != POINTB
            DISTANCE = COMPUTE_DISTANCE(POINTA, POINTB)
            if DISTANCE < MINIMUM
                MINIMUM = DISTANCE
                POINT1 = POINTA
                POINT2 = POINTB
            end if
        end if
    end loop
end loop
```

Looking at this code, if we have $N$ points, it would take $N^2$ steps to solve the problem! That's not very efficient, event for a small data set. However, the code itself is really simple, and it is guaranteed to find exactly the best answer, provided we have enough time and a powerful enough computer to run the program.

In the project for this module, we'll implement a few different brute-force algorithms to solve simple problems. This will help us gain more experience with this particular technique. 
