---
title: Sliding Window Summary
date: 2019-11-10 08:56:40
tags:
description: This is a summary of sliding window problems in Leetcode. It turns out a general template can be extracted. There are two types of sliding window problems. One is to find the shortest or longest substring or subarray, the other is to find the number of subarrays satisfies some requirements.
---

### Part 1. Longest or shortest substring or subarray

* LC 3, Longest substring without repeating characters
  Use a hashtable to store the rightmost index of each character. When encountering a repeated character, the left boundary is moved to the rightmost index of this character.
* LC 159, Longest substring with at most two distinct characters
* LC 340, Longest substring with at most K distinct characters
  It's reduced to  LC 159 with K = 2.
* LC 978, Longest Turbulent Subarray 
* LC 76, Minimum window substring
* LC 424, Longest repeating substring replacement
* LC 576, Permutation in string
* LC 1004, Max consecutive ones III. Similar to LC 424
*  LC,1208, Get Equal Substrings Within Budget 

### Part 2. Number of subarrays satisfying some requirements

* LC 992, Subarrays with K different integers
  `exact K = atMost(K) - atMost (K - 1)`
* LC 1074, Number of submatrices that sum to target
* LC 1248, Count number of nice subarrays

### Part 3. Maximum or minimum of subarrays

* LC 239, Sliding window maximum
* LC 1052, Grumpy bookstore owner

### Part 4. Other

* LC 1176, Diet plan performance
* 



