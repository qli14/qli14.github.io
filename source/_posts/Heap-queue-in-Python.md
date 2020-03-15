---
title: Heap queue in Python
mathjax: true
date: 2020-02-28 16:44:06
tags:
description: A note about the heap queue in Python (or priority queue). I encountered several Leetcode problems related to heap queue before, but still I'm not quite familiar with the implementation and usage. Recently, I tried to solve LC 1354 Construct target arrays with multiple sums, which is also a heap queue related problem.
mathjax: True
---

### What\'s heap queue?

Heap queue is essentially a binary tree with the value of a parent node less than or equal to its children. Thus the root has the smallest value. This data structure is useful when we need to maintain a sorted array of values. For example in LC 1354, I could come up the overall idea of finding the max in the array and pushing the updated value back into the array. A brute force method would lead to a time complexity of $O(N\log (N) N \log (N))$. That's why the heap queue is a suitable data structure for this problem.

 ### Basic implementation in Python

* Convert a list to heapq

```python
heapq.heapify()
```

* Pop up the smallest value

```python
heapq.heappop()
```

* Push the value item onto the heapq

```
heapq.heappush(heapq, item)
```

### Related problems

* LC 1354 Construct Target Array With Multiple Sums
* LC 1353 Maximum number of events that can be attended

