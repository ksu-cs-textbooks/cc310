---
title: "Strings Introduction"
pre: "1. "
weight: 11
date: 2019-02-04T10:53:26-05:00
hidden: true
---

{{< youtube zcCtPamophM >}}

#### Resources

* <a href="slides" target="_blank">Slides</a>

#### Video Script


[Slide 1]

Throughout this course we will look at many types of data structures. 

[Slide 2]

We have already seen a handful of structures in CC 310. In that course, we looked at the structures, how they worked such as accessing elements and determining sizes. We also looked at how we would implement our own versions of those structures. This course will follow a similar pattern as we work through new data structures. 

[Slide 3]

To start the course, we begin with an often overlooked but important data structure: strings. They are a very natural choice of data structure as there exists a lot of text based data. This data can be social media posts, product reviews, abstracts, and so much more. 

[Slide 4]

The field of data science is rapidly growing and has many applications that benefit from text analysis. These tasks include: sentiment analysis, recommendation networks, categorization and classification, just to name a few. 

[Demo]
<!---
Here I would like to include an ad-libbed small demo of the https://projector.tensorflow.org/ finding similar words. 
-->

In terms of real world application, Tensorflow is a Python package for natural language processing. Many researchers in industry and academia use Tensorflow and its pre-trained models to various tasks, like sentiment analysis and categorization. The developers of Tensorflow have built this visualizer at projector.tensorflow.org which is quite interesting to look at. They have used machine learning to determine which words are most related. Here we can look at 'cat' and we see some words that are very intuitively related to cat: mouse, dog, tiger, animal... Then there are some that maybe aren't immediately clear: blue (for blue catfish), like (for cat like reflexes)

[Slide 4]

While these tasks have very different goals, they are similar in the fact that they require an efficient way to work with text based data. In the second section of the module, we will discuss how to handle strings and some complications they present. 
