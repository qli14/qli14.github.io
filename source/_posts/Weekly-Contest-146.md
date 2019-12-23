---
title: Weekly Contest 146
date: 2019-07-21 11:45:36
tags:
mathjax: True
description: Leetcode weekly contest 146. Solved the first problem and had no idea about the rest.
---

### Number of equivalent domino pairs

Brute force with $O(N^2)$ leads to TLE. 

Then I used a hash map to count the frequency of the equivalent dominoes. Note that list in python is not hashable so that the keys in the dictionary are tuples.

```python
class Solution(object):
    def numEquivDominoPairs(self, dominoes):
        """
        :type dominoes: List[List[int]]
        :rtype: int
        """
        result = 0
        dict1 = {}
        for domino in dominoes:
            if (domino[0], domino[1]) in dict1:
                result += dict1[(domino[0], domino[1])]
                dict1[(domino[0], domino[1])] += 1
            elif (domino[1], domino[0]) in dict1:
                result += dict1[(domino[1], domino[0])]
                dict1[(domino[1], domino[0])] += 1
            else:
                dict1[(domino[0], domino[1])] = 1
        return result
```

When counting the frequency of elements, people usually use `collections.Counter()`.

```Python
class Solution(object):
    def numEquivDominoPairs(self, dominoes):
        """
        :type dominoes: List[List[int]]
        :rtype: int
        """
        result = 0
        dominoes_tuple = [tuple(sorted(domino)) for domino in dominoes]
        for v in collections.Counter(dominoes_tuple).values():
            result += v * (v - 1) / 2
        return result
```

### Shortest path with alternating colors

To find the shortest path, use BFS.

https://leetcode.com/problems/shortest-path-with-alternating-colors/discuss/339964/Python-BFS

Can't understand the solution.

The graph is encoded in a list.

### Minimum cost tree from leaf values

**DP solution first** 

```Python
def mctFromLeafValues(self, arr):
        """
        :type arr: List[int]
        :rtype: int
        """
        n = len(arr)
        dp = [[float('inf')] * n for _ in range(n)]
        
        for c in range(0, n):
            for i in range(0, n - c):
                j = i + c
                if c == 0:
                    dp[i][j] = 0
                else:
                    for k in range(i, j):
                        dp[i][j] = min(dp[i][j], max(arr[i:k+1]) * max(arr[k+1:j+1]) + dp[i][k] + dp[k+1][j])
        return dp[0][n-1]
```

**How about $O(N)$ time and space?**

[Lee's solution](https://leetcode.com/problems/minimum-cost-tree-from-leaf-values/discuss/339959/One-Pass-O(N)-Time-and-Space)



### Maximum of absolute value expression

**Problem statement:**Find the maximum of the following expression

$$|x[i] - x[j]| + |y[i] - y[j]| + |i - j|$$

**Solution 1**

https://leetcode.com/problems/maximum-of-absolute-value-expression/discuss/340051/Python-very-intuitive-math-solution-with-explanation-O(N)

This math solution is easy to understand.

We can assume $i < j$ and the above expression can be divided into four situations

```python
if x[i] > x[j]:
    if y[i] > y[j]:
    	x[i] - x[j] + y[i] - y[j] + i - j
        = (x[i] + y[i] + i) - (x[j] + y[j] + j)
    else:
        x[i] - x[j] + y[j] - y[i] + i - j
        = (x[i] - y[i] + i) - (x[j] - y[j] + j)
else:
    if y[i] > y[j]:
    	x[j] - x[i] + y[i] - y[j] + i - j
        = (-x[i] + y[i] + i) - (-x[j] + y[j] + j)
    else:
        x[j] - x[i] + y[j] - y[i] + i - j
        = (-x[i] - y[i] + i) - (-x[j] - y[j] + j)
Find max and min of four expressions
(x[i] + y[i] + i)
(x[i] - y[i] + i)
(-x[i] + y[i] + i)
(-x[i] - y[i] + i)
```

Code

```python
class Solution(object):
    def maxAbsValExpr(self, arr1, arr2):
        """
        :type arr1: List[int]
        :type arr2: List[int]
        :rtype: int
        """
        res = 0
        max1 = [float('-inf')] * 4
        min1 = [float('inf')] * 4
        for i in range(len(arr1)):
            max1[0] = max(max1[0], arr1[i] + arr2[i] + i)
            min1[0] = min(min1[0], arr1[i] + arr2[i] + i)
            max1[1] = max(max1[1], -arr1[i] + arr2[i] + i)
            min1[1] = min(min1[1], -arr1[i] + arr2[i] + i)
            max1[2] = max(max1[2], arr1[i] - arr2[i] + i)
            min1[2] = min(min1[2], arr1[i] - arr2[i] + i)
            max1[3] = max(max1[3], -arr1[i] - arr2[i] + i)
            min1[3] = min(min1[3], -arr1[i] - arr2[i] + i)
        for i in range(4):
            res = max(res, max1[i] - min1[i])
        return res
```

**Solution 2** 

[Lee's solution](https://leetcode.com/problems/maximum-of-absolute-value-expression/discuss/339968/JavaC%2B%2BPython-Maximum-Manhattan-Distance)

The coding is exactly the same, but with a different intuition.























































