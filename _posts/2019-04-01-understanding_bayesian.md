---
title: "Understanding the Bayesian way"
date: 2019-04-01
permalink: /posts/2019/04/blog-post-12/bayesian-way
redirect_from: /posts/2019/04/blog-post-12/
tags:
  - bayes theorem
  - statistics
  - data analysis
---

Imagine that you are feeling some symptoms for a particular disease and during checkup a doctor suggests you take a test, which would tell (with 99% accuracy) if you have a rather rare disease (only 0.1% people have it). Is it worth to be curious? What would you do if you test positive? The test is 99% accurate!

Now imagine that you have a set of 1000 people. Only one of them (0.1%) will have this disease and there is a rather significant probability that he will test positive. Likely 10 people, out of 999 healthy people, will also test positive (1%). So, in the end, you have 11 positive results and only 1 sick person in the group. So actually there is only 9% chance that you actually have this disease.

This "paradox" is not a mathematical paradox, nor it's a mathematical trick. It’s a Bayesian trap!

The detailed explanation of the above problem is described in here:

Now we head towards thinking how well the algorithm performs in certain conditions and how poor in other conditions-

<center><img src = "https://github.com/theAayushbajaj/theaayushbajaj.github.io/blob/master/_posts/img/bayesian/note-1.png" width = "500"></center>
<center><img src = "https://github.com/theAayushbajaj/theaayushbajaj.github.io/blob/master/_posts/img/bayesian/note-2.png" width = "500"></center>


**Pros**:

It is fast than most of the learning algorithms to predict a class of test dataset
Assuming that there is no correlation among variables or features in the data (which is practically not possible) Naive Bayes performs pretty well with decent accuracy score than other models.
Performs really well when the data is categorical.
Naive Bayes can be used for Binary and Multiclass Classification.
Great choice for Text Classification problems. It’s a popular choice for spam email classification.
Cons:

->Zero frequency condition:

If a categorical variable has a category that is observed in the test dataset and is not present in the training set then Naive Bayes will assign zero probability to it and eventually it will be unable to make a prediction.

Methods have been devised to solve such zero frequency conditions:

Various Smoothening techniques such as,

Laplace estimator
Adding 1 for each class category
->The most important of all is the algorithms assumption for the features to have no correlation. Since the condition it assumes doesn't occur naturally.So, this estimator is not considered good for industry level practice.

Gaussian Naive Bayes

When attribute values are continuous, an assumption is made that the values associated with each class are distributed according to Gaussian i.e., Normal Distribution.

If in our data, an attribute say “x” contains continuous data. We first segment the data by the class and then compute mean and Variance of each class.

<center><img src = "https://github.com/theAayushbajaj/theaayushbajaj.github.io/blob/master/_posts/img/bayesian/note-3.png" width = "500"></center>


**MultiNomial Naive Bayes**

MultiNomial Naive Bayes is preferred to use on data that is multinomially distributed. It is one of the standard classic algorithms. Which is used in text categorization (classification). Each event in text classification represents the occurrence of a word in a document.

**Bernoulli Naive Bayes**

Bernoulli Naive Bayes is used on the data that is distributed according to multivariate Bernoulli distributions.i.e., multiple features can be there, but each one is assumed to be a binary-valued (Bernoulli, boolean) variable. So, it requires features to be binary valued.

**Real World application for Naive Bayes-**

Text Classification - NB algorithm gives very good results in text classification Eg Spam Classification, Sentiment Analysis
Since its an eager learning classifier it can be used for Real-Time prediction.
It also finds its application in Credit Scoring for e-learning platforms.
Can also be used in Recommendation Systems.