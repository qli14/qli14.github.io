---
title: Weekly Contest 156
date: 2019-09-28 23:13:43
tags:
description: For the first time I could solve three problems. TLE on the last one.
---

### 1207. Unique number of occurrences

Check the duplicates in the frequencies

### 1208. Get equal substrings within budget

Sliding window.

### 1209. Remove all adjacent duplicates in string II

Repeatedly find the intervals within which the substrings need to be removed.

### 5208. Minimum moves to reach target with rotations.

TLE.

BFS method. Be careful about the visited status.

```python
def minimumMoves(self, grid: List[List[int]]) -> int:
        # BFS
        n = len(grid)
        levels = {(0, 0, 0, 1)}
        target = (n - 1, n - 2, n - 1, n - 1)
        move = 0
        visited = set()
        while levels:
            next_levels = set()
            for level in levels:
                r1, c1, r2, c2 = level
                visited.add((r1, c1, r2, c2))
                if r1 == r2:
                    if c2 + 1 < n and grid[r2][c2 + 1] == 0:
                        if (r2, c2, r2, c2 + 1) not in visited:
                            next_levels.add((r2, c2, r2, c2 + 1))
                    if r1 + 1 < n and grid[r1 + 1][c1] == 0 and grid[r2 + 1][c2] == 0:
                        if (r1 + 1, c1, r2 + 1, c2) not in visited:
                            next_levels.add((r1 + 1, c1, r2 + 1, c2))
                        if (r1, c1, r1 + 1, c1) not in visited:
                            next_levels.add((r1, c1, r1 + 1, c1))
                if c1 == c2:
                    if r2 + 1 < n and grid[r2 + 1][c2] == 0:
                        if (r2, c2, r2 + 1, c2) not in visited:
                            next_levels.add((r2, c2, r2 + 1, c2))
                    if c2 + 1 < n and grid[r1][c1 + 1] == 0 and grid[r2][c2 + 1] == 0:
                        if (r1, c1 + 1, r2, c2 + 1) not in visited:
                            next_levels.add((r1, c1 + 1, r2, c2 + 1))
                        if (r1, c1, r1, c1 + 1) not in visited:
                            next_levels.add((r1, c1, r1, c1 + 1))
            # print(next_levels)
            if target in next_levels:
                return move + 1
            levels = next_levels
            move += 1
        return -1
```

