---
title: Biweekly contest 12
date: 2019-11-06 11:21:11
tags:
description: Virtual contest. Solved the first two
---

### 1245 Tree Diameter

[lee215 solution](https://www.youtube.com/watch?v=KQmK3NcypEg)

```python
# -*- coding: utf-8 -*-
"""
Created on Wed Nov  6 11:04:01 2019

@author: qli14
"""
import collections
dict1 = collections.defaultdict(set)
edges = [[0, 1], [1, 2], [2, 3], [1, 4], [4, 5]]
#edges = [[0, 1], [0, 2]]
for u, v in edges:
    dict1[u].add(v)
    dict1[v].add(u)
#print(dict1)

def dfs(u, v):
    if not dict1[v]:
        return 0
    if (u, v) in memo:
        return memo[u, v]
    res = 0
    for w in dict1[v]:
        if w == u: continue # don't go backwards
        res = max(res, dfs(v, w))
    memo[u, v] = res + 1
    return res + 1

# use memorization to avoid repeated calculation of dfs(u, v)
memo = {}
res = 0
for u, v in edges:
    res = max(res, dfs(u, v) + dfs(v, u) - 1)
print(res)
print(memo)
```

### 1246 Palindrome removal

