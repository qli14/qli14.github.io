---
title: Biweekly Contest 14
date: 2019-12-02 16:51:43
tags:
description: (2/4) Stuck in the second problem about binary search. Can't think about the problem very clearly. Need to summarize the binary search.
---

### 1271. Hexspeak

Quite trivial. Just code

### 1272. Remove interval

A typical binary search problem, but was stuck in finding the starting and ending position of the interval.

In an increasing array, there could be several different searching for a `target`

* Find the last element smaller than target
* Find the first element larger than target

```python
while l < r:
    mid = l + (r - l) // 2
    if mid < target:
        l = mid + 1
    else:
    	r = mid
while l < r:
    mid = (l + r + l) // 2
    if mid < target:
        l = mid
    else:
    	r = mid - 1
```

In order to avoid endless loops, only the above two versions are possible.

### 1273. Delete tree nodes

Convert the problem to N-ary tree

### 1274. Number of ships in a rectangle

Didn't have time to try during the contest