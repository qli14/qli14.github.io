---
title: Weekly Contest 150
date: 2019-08-18 12:32:38
tags:
description: Solved the first two. Stuck in the third one
---

### Find words that can be formed by characters

Use a dictionary to count the occurrences of each letter.

### 1161. Maximum level sum of a binary tree

DFS

BFS is more intuitive. Calculate the sum level by level.

### 1162. As far from land as possible

TLE with brute force.

[DFS solution](https://leetcode.com/problems/as-far-from-land-as-possible/discuss/360963/C%2B%2B-with-picture-DFS)

This I got max recursion in the case of all lands. The problem is land cell shouldn't be updated.

A better BFS solution from the same link by maintaining a deque.  Why does BFS work?

```python
def maxDistance(self, grid):
        """
        :type grid: List[List[int]]
        :rtype: int
        """
        # BFS
        # use a deque to maintain the level in BFS
        n = len(grid)
        
        q = collections.deque([(i, j) for i in range(n) for j in range(n) if grid[i][j] == 1])
        # print(q)
        if len(q) == n * n or len(q) == 0: return -1
        level = 0
        direcs = [(1, 0), (-1, 0), (0, 1), (0, -1)]
        while q:
            size = len(q)
            for _ in range(size):
                x, y = q.popleft()
                for direc in direcs:
                    xi = x + direc[0]
                    yj = y + direc[1]
                    if 0 <= xi < n and 0 <= yj < n and grid[xi][yj] == 0:
                        q.append((xi, yj))
                        grid[xi][yj] = 1 # mark visited
            level += 1
        return level - 1
```



### 1163. Last substring in lexicographical order

Tried to use a que to maintain the indices of comparison, but TLE.

Get the idea to [swallow the unecessary searching](https://leetcode.com/problems/last-substring-in-lexicographical-order/discuss/361121/Python-O(n)-with-explanation). 

```python
def lastSubstring(self, s):
        """
        :type s: str
        :rtype: str
        """
        # start with the last letter
        max_letter = 'a'
        idx = []
        for i in range(len(s)):
            if ord(s[i]) == ord(max_letter):
                idx.append(i)
            elif ord(s[i]) > ord(max_letter):
                max_letter = s[i]
                idx = [i]
        
        # if len(idx) == 1: return s[idx[0]:]
        
        # We have at least two candidates
        # compare later letters
        # q = collections.deque(idx)
        q = idx
        
        k = 0
        
        while len(q) > 1:
            size = len(q)
            max_letter = 'a'
            idx = []
            for i in range(size):
                # j = q.popleft()
                j = q[i]
                # How to filter or swallow?
                if i - 1 >= 0 and q[i - 1] + k == j:
                    continue
                
                if j + 1 < len(s) and s[j + 1] == max_letter:
                    idx.append(j + 1)
                elif j + 1 < len(s) and ord(s[j + 1]) > ord(max_letter):
                    max_letter = s[j + 1]
                    idx = [j + 1]
            # q = collections.deque(idx)
            q = idx
            k += 1
        # Finally, only one index in q
        # return s[q.popleft() - k :]
        return s[q[0] - k :]
```

