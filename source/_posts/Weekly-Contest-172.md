---
title: Weekly Contest 172
mathjax: true
date: 2020-01-19 19:23:39
tags:
description: (4/4) Didn't participate the weekly and biweekly contests of last week. Not in good shape. Finished this week's contest with about 10 mins left.
---

### 1323. Maximum 69 number

Just replace the first 6 from left to right by 9.

### 1324. Print words vertically

Be careful about the trailing spaces.

### 1325. Delete leaves with a given value

My idea is to check whether there is leaf nodes with given value until this type of leaf nodes don't exist.

The recursion solution by [Lee215](https://leetcode.com/problems/delete-leaves-with-a-given-value/discuss/484264/JavaC%2B%2BPython-Recursion-Solution) is much more elegant.

### 1326. Minimum number of taps to open to water a garden

I eliminated intervals that are contained in another interval and then sorted the intervals increasingly based on the starting point and decreasingly based on the ending point. Also the starting point needs to be truncated to 0 if it's negative. 

After that, a binary search method is used to find the minimum number of taps. 

Similar problem: 1024 Video stitching

How to understand the dynamic programming solution by lee215?

Also, how to understand the similarity with LC 45 Jump Game II? (huahua, Youtube)

