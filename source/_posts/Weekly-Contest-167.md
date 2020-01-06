---
title: Weekly Contest 167
date: 2019-12-16 13:01:46
tags:
description: (2/4) TLE on the third problem. Failed to work it out. No time for the last one.
mathjax: true
---

### 1292. Maximum side length of a square with sum less than or equal to threshold

I started with a brute-force method, time complexity $O(N^3)$, but TLE.

There are two possible solutions. One is the sliding window along the diagonals, the other is dp combined with binary search since the elements are all non-negative.

### 1293. Shortest path in a grid with obstacles elimination

A typical BFS with deque.