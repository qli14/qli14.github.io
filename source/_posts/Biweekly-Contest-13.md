---
title: Biweekly Contest 13
date: 2019-11-17 08:30:11
tags:
description: (2/4) Stuck in the third problem. Tried to obtain the connected component with dfs.
---

### 1256. Encode Number

My observation is that `f(n)` is obtained by setting `f(2^m - 1)` to '0' * m, followed by the addition of `n - (2^m - 1)`. Note that the leading zeros are kept. Thus the result is a string with length `m`.

### 1257. Smallest common region

This problem is to find the lowest common ancestor (LCA) of two given node in N-ary tree. The main difference is that we can access the parent of a node in this problem. So my idea is to find the path to the root for each given node and then find the LCA from the root.

### 1258. Synonymous Sentences

I got the idea of find all the equivalents and sort them, but was stuck in obtaining the connected components with dfs. 

#### Method 1. Union-find. 

Then all the synonyms of a word can be accessed through its root. All the rest is just a typical back tracking process.

#### Method 2. BFS

#### Method 3. DFS

### 1259. Handshakes That Don't Cross

Didn't have time to try. Feels like a dp problem.





