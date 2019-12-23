---
title: Weekly Contest 157
date: 2019-10-07 16:01:26
tags: DP
description: Solved the first two. Got problem about marking the visited cells in the third problem.
---

### Play with chips

min(odd, even)

### Longest arithmetic subsequence of given difference

TLE with brute force method.

Use a hashmap

### Path with max gold

TLE with the idea of recording all paths. Optimized the calculation of gold slightly and passed all test cases, although quite slow (15.65%). I tried dfs during the contest, but the visited mark caused problem. It turns out that the visited mark should be reset after dfs.

Try the dfs again later. The key part is to mark the cell as visited and reset it after dfs.

```python
def getMaximumGold(self, grid: List[List[int]]) -> int:
        # dfs
        def dfs(i, j):
            if grid[i][j] == 0: return 0
            result = 0
            temp = grid[i][j]
            grid[i][j] = 0
            
            if i > 0: result = max(result, temp + dfs(i - 1, j))
            if j > 0: result = max(result, temp + dfs(i, j - 1))
            if i + 1 < m: result = max(result, temp + dfs(i + 1, j))
            if j + 1 < n: result = max(result, temp + dfs(i, j + 1))
            
            # reset grid[i][j]
            grid[i][j] = temp
            return result
        
        m = len(grid)
        n = len(grid[0])
        result = 0
        for i in range(m):
            for j in range(n):
                result = max(result, dfs(i, j))
        return result
```

**Task:** write a short summary about the dfs related problems.

- Number of islands
- Path with max gold
- Minesweeper

### Count vowels permutation

Back tracking leads to TLE.

DP works well. 

```python
# Two different ways of initialization
# Be careful
a = [[0] * 5] * 4
b = [[0] * 5 for _ in range(4)]
a[2][3] = 100
b[2][3] = 100
print(a)
# [[0, 0, 0, 100, 0], [0, 0, 0, 100, 0], [0, 0, 0, 100, 0], [0, 0, 0, 100, 0]]
print(b)
# [[0, 0, 0, 0, 0], [0, 0, 0, 0, 0], [0, 0, 0, 100, 0], [0, 0, 0, 0, 0]]
```

