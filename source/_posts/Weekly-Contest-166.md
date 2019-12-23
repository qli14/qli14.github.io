---
title: Weekly Contest 166
date: 2019-12-07 21:46:25
tags:
description: (4/4) The first two are quite trivial. The third one is a typical binary search quesiton. I was stuck in the last one for a while. Later I realized the size of the matrix is at most 3 by 3. Thus a brute force searching is possible with back tracking. Finished the contest with around 1 hour.
---

### 1283. Find the smallest divisor given a threshold

Binary search. Similar to shipping weight, divide chocolate, etc.

### 1284. Minimum number of flips to convert binary matrix to zero matrix

Brute force searching with back tracking.

Only need to count the number of flips for each elements. The number of flips must be even (odd) if the element is 0 (1).

One problem I encountered is passing a copy of the nested list into the back tracking function. In fact, a deepcopy is necessary, otherwise, it's just a reference.

The assignment operator in Python doesn't create a new variable but shares the reference of the original object. [copy in Python](https://www.geeksforgeeks.org/copy-python-deep-copy-shallow-copy/) 

