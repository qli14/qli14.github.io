---
title: Weekly Contest 161
date: 2019-11-07 09:32:26
tags:
description: Virtual contest. Solved the first three. For the last one, I was stuck in extending the Bezout's identity to n numbers.
mathjax: True
---

###  1247. Minimum Swaps to Make Strings Equal 

Count the number of occurrences with x or y in the first string, `countx`, and `county`.

One swap can reduce `countx`  or `county` by 2.

Two swaps can reduce `countx` and `county` by 1 at the same time.

###  1248. Count Number of Nice Subarrays   

My solution during the contest was counting the number of nice subarrays sequentially. For example, s[i] and s[j] are odd and there are exactly k odd numbers in between (including i and j). Suppose s[p] is the first odd number to the left of s[i] and s[q] is the first odd number to the right of s[j], the number of odd subarrays is $(i - p) \times (q - j)$.

A better perspective (it's actually slower than my solution) is the sliding window solution by [lee215](https://leetcode.com/problems/count-number-of-nice-subarrays/discuss/419378/JavaC%2B%2BPython-Sliding-Window-atMost(K)-atMost(K-1)). Exactly k times = at most k time - at most (k - 1) times.

###  1249. Minimum Remove to Make Valid Parentheses 

Typical stack problem.

###  1250. Check If It Is a Good Array 

Bezout identity. This problem is equivalent to check whether the greatest common divisor (gcd) is one.

