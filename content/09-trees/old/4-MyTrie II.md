---
title: "MyTrie II"
weight: 20
pre: "4. "
---
### Getters 

{{< youtube su-hJ1CDY3M  >}}


#### Getting word count 
For this function, we want to get the total number of words that are contained within our trie. We will fan out through all of the children and count all of the nodes that have their `is_word` attribute equal to true. 

```tex
function WORDCOUNT()
    COUNT = 0
    if is_word
        COUNT = 1
    for CHILD in CHILDREN
        COUNT += CHILD.WORDCOUNT()
    return COUNT
end function
```

#### Get max word length 
Next, we want to get the longest word contained in our trie. To do this, we will recurse each child and find the maximum length of the child. 
- Base Case: we are at a leaf and it is a word, return 0
- Recursive Case: declare a maximum of -1 for a tracker and then for each child run the maximum word length function on it. If the value returned from the child is greater than our maximum tracker, set the tracker equal to the value. Once we have iterated all of the children, return the maximum tracker plus one. 

```tex
function MAXWORD()
    if LEAF and is_word
        return 0
    else
        MAX = -1
        for CHILD in CHILDREN
            COUNT = CHILD.MAXWORD()
            if COUNT greater than MAX
                MAX = COUNT
        return MAX + 1
end function
```

#### Get completions 

{{< youtube urFTpJwqRVY  >}}


This function will act as an auto-complete utility of sorts. A user will input a string of characters and we will return all of the possible words that are contained in our trie. This will happen in two phases. First, we traverse the trie to get to the end of the input string (lines 1-12). The second portion then gets all of the words that are contained after that point in our trie (lines 14-21).

```tex
function COMPLETIONS(WORD)
1.    if WORD length greater than 0
2.        FIRST = first character of WORD
3.        REMAIN = remainder of WORD
4.        CHILD = FINDCHILD(FIRST)
5.        if CHILD is none
6.            return []
7.        else
8.            COMPLETES = CHILD.COMPLETIONS(REMAIN)
9.            OUTPUT = []
10.            for COM in COMPLETES
11.                append CHILD.item + COM to OUTPUT
12.            return OUTPUT
13.    else
14.        OUTPUT = []
15.        if is_word
16.            append ITEM to OUTPUT
17.        for CHILD in CHILDREN
18.            COMPLETES = CHILD.COMPLETIONS("")
19.            for COM in COMPLETES
20.                append CHILD.item + COM to OUTPUT
21.        reutrn OUTPUT
end function
```
