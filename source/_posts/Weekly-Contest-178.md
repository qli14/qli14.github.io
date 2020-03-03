---
title: Weekly Contest 178
mathjax: true
date: 2020-03-02 21:32:50
tags:
description:(3/4). Rank 1867. The first two problem are trivial. I was stuck in the third problem for too long a time. The basic idea was not right, leading to TLE.
---

### 1367. Linked List in Binary Tree

If the current values in the tree and linked list are different, check whether the linked list is a sub-path of the left and right trees. If they are the same, note that the path in the tree must be continuous. This is where I was stuck during the contest.

### 1378. Minimum Cost to Make at Least One Valid Path in a Grid

I thought about dp first, but actually not working. This can be solved with deque to find the minimum cost. The key here is to avoid repeated visiting, otherwise, TLE.

Similar problems with deque:

* To be added