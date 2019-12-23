---
title: Weekly Contest 164
date: 2019-11-24 09:05:39
tags:
description: (2/4) Solved the first two. For the last problem, my method of 2d dp needs to be reduced to 1d. In 1d dp, I got TLE for one test case in which the array length is much larget than the steps. The important thing is to initialize dp as min(arrLen, steps + 1). The third problem is about Trie. Need to study some basics first.
---

### 1266. Minimum time visiting all points

Note that the diagonal move includes both diagonal and anti-diagonal moves.

### 1267. Count servers that communicate

Union find

### 1268. Search suggestions system

A typical Trie problem. Didn't try during the contest.

### 1269. Number of ways to stay in the same place after some steps

During the contest, I figured out the 2d dp solution and then reduced to 1d dp due to MLE.

Still I got TLE in the last test case in which the array length is much larger than steps. The trick is the largest index one can reach is n with n steps. So all the indices beyond n is useless.