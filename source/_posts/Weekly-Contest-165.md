---
title: Weekly Contest 165
date: 2019-12-07 11:16:07
tags:
mathjax: true
description: (2/4) Stuck in the third problem with TLE. I used a similar question about counting the number of sub matrices with target sum as a reference. The time complexity is O(N^3), while the expected time compelxity is O(N^2). Didn't have time to try the last one.
---

### 1275. Find winner on a tic tac toe game

Record the number of stones in each row, each column, and two diagonals.

### 1276. Number of burgers with no waste of ingredients

Quite trivial

### 1277. Count square submatrices with all ones

I used the question about counting the number of submatrices with target sum as the reference.

At first, I missed the condition of square submatrices and got TLE. Later, I couldn't reduce the time complexity to $O(N^2)$.

This is actually a dp problem by find the largest square with all ones with (i, j) as the upper left or bottom right corner. [lee215's solution](https://leetcode.com/problems/count-square-submatrices-with-all-ones/discuss/441306/Python-DP-solution)

### 1278. Palindrome partitioning III

Didn't try during the contest. 

DP with dp inside? Huahua, leee215.