---
title: Biweekly Contest 21
mathjax: true
date: 2020-03-09 00:04:04
tags:
description: (2/4) Rank 958. I was stuck in the first problem. For the second one, my first thought was sliding window, but actually not working. Solved the third one and no time for the last problem.
---

### 1370. Increasing  Decreasing String

I implemented a naïve method by sorting the remaining characters every time.

### 1371. Find the Longest Substring Containing Vowels in Even Counts

Think about this problem starting with only one vowel in consideration. We can just count mark the even or odd count at every position. To find the longest substring with the count even, the count must be the same in odd or even in the left and right bounds. 

This idea can be extended to multiple vowels by using a bitmask to represent the status of multiple vowels in each position.

### 1372. Longest ZigZag Path in a Binary Tree

A typical tree problem solved with recursion

### 1373. Maximum Sum BST in Binary Tree

No time to try this problem during the contest. Later solved it by referring to a [solution](https://leetcode.com/problems/maximum-sum-bst-in-binary-tree/discuss/531800/Python-Easy-traversal-with-explanation) in Leetcode. I misunderstood the problem with the input as a BST.

