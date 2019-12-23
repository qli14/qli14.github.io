---
title: Weekly-Contest-147
date: 2019-07-28 11:36:02
tags: dp
description: Solved the first two
mathjax: True
---

### N-th Tribonacci Number
Trivial
### Alphabet Board Path
Trivial
### 1139. Largest 1-bordered Square
[lee215](https://leetcode.com/problems/largest-1-bordered-square/discuss/345233/JavaC%2B%2BPython-Straight-Forward)
Track the number of continuous 1s along the rows and columns. Then loop over the side length in the descending order to find the largest side length. The number of elements is the square of the side length.

```Python
def largest1BorderedSquare(self, grid):
        """
        :type grid: List[List[int]]
        :rtype: int
        """
        # For the element at (i, j)
        # top[i][j]: the number of continous 1s from top
        #       top is initialized to be grid first
        #       if i > 0 and top[i][j] == 1:
        #               top[i][j] = top[i-1][j] + 1
        # left[i][j]: the number of continous 1s from left
        #       left is initialized to be grid first
        #       if j > 0 and left[i][j] == 1:
        #               left[i][j] = left[i][j-1] + 1
        
        top = [a[:] for a in grid]
        left = [a[:] for a in grid] # can't do left = grid since the original grid would be changed when updating left and top
        m = len(grid)
        n = len(grid[0])
        
        for i in range(m):
            for j in range(n):
                if i > 0 and top[i][j] == 1:
                    top[i][j] = top[i-1][j] + 1
                if j > 0 and left[i][j] == 1:
                    left[i][j] = left[i][j-1] + 1
        # print(top, left)
        # The largest possible side length is min(m, n)
        for r in range(min(m, n), 0, -1):
            # try to find the square with side length r
            # starting position (upper left corner)
            # is (i, j)
            # lower right position is then
            # (i + r - 1, j + r -1)
            # i + r - 1 < m => i < m - r + 1
            # j + r - 1 < n => j < n - r + 1
            for i in range(m - r + 1):
                for j in range(n - r + 1):
                    # see if (i, j) satisfy the condition
                    if top[i + r - 1][j] >= r and top[i + r - 1][j + r - 1] >= r and left[i][j + r - 1] >= r and left[i + r - 1][j + r - 1] >= r:
                        return r * r
        return 0
```

**Note:** When initializing  `top` and `left`, it must be `a[:]` instead of `a`, otherwise, it just copies the reference to the list, rather than the actual list.

**Similar problem** 221. Maximal Square.

I tried with a similar method to count the number of continuous 1s, but TLE. Also, be careful about the indexing of 2D list. For example, 

```python
A = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
print(A[0:2][2])
    # The result is 'list index out of range'
# A[0:2] gives [[1, 2, 3], [4, 5, 6]]
# in order to get the second column of the first two rows
print([a[1] for a in A[0:2]])
	# The result is [2, 5]
```

Still this problem can be solved with dp, with the `dp[i][j]` representing the largest side length form (0, 0) to (i, j).

```python
def maximalSquare(self, matrix):
        """
        :type matrix: List[List[str]]
        :rtype: int
        """
        m = len(matrix)
        if m == 0: return 0
        n = len(matrix[0])
        
        dp = [[0] * n for _ in range(m)]
        
        best = 0
            
        for i in range(m):
            for j in range(n):
                if i == 0: dp[0][j] = int(matrix[0][j])
                if j == 0: dp[i][0] = int(matrix[i][0])
                if i > 0 and j > 0 and matrix[i][j] == '1':
                    dp[i][j] = min(dp[i-1][j], dp[i-1][j-1], dp[i][j-1]) + 1
                best = max(best, dp[i][j])
        return best * best
```

### Stone Game II

DFS.
```python
def stoneGameII(self, piles):
        """
        :type piles: List[int]
        :rtype: int
        """
        n = len(piles)
        dict1 = {}
        def dfs(i, M):
            # starting from index i and 1 <= X <= 2M
            # return the difference in the number of stones
            # between the first player and the second player
            # if both players play properly.
            
            # player1 - player2 = dfs(0, 1)
            # player1 + player2 = sum(piles)
            # player1 = (sum(piles) + dfs(0, 1)) / 2
            if (i, M) in dict1: return dict1[i, M]
            best = float('-inf')
            # best = 0
            if i == n:
                return 0
            if i + 2 * M >= n: # take all if the number of remaining piles is less than 2M
                return sum(piles[i:])
            for X in range(1, 2 * M + 1):
                # print(i, X, M)
                best = max(best, sum(piles[i:i+X]) - dfs(i+X, max(M, X)))
            dict1[i, M] = best
            return best
        return (sum(piles) + dfs(0, 1)) / 2
```

**Note 1:** `best` must be initialized to `-inf` since the score returned by `dfs(i, M)` could be a negative number. That is to say, the player taking stone first is not guaranteed to win.

**Note 2:** Use a dictionary to store the returned value of `(i, M)` to avoid repeated calling of `dfs(i, M)`.

### Convert to base negative 2

Use the series expansion. In general, the base can be 2 or -2.
$$N = \sum_{i=0}^{m} a[i]b^i$$
in which $N$ is the input number to be converted, $a[i]$ is the $i$th digit of the final result, and $b=\pm 2$ is the base. The problem is converted to find the coefficients $a[i]$.

$$N = a[0]+\sum_{i=1}^{m} a[i]b^i$$

So that $a[0] = N \% b$ and $N$ is updated as

$$N=(N - a[0])/b=\sum_{i=1}^{m} a[i]b^{i-1}=a[1] + \sum_{i=2}^{m} a[i]b^{i-1}$$

Similarly, $a[1] = N\%b$ and $N$ is updated as 

$$N = (N-a[1])/b$$

All the coefficients can be calculated by repeating the above two steps.

```python
def baseNeg2(self, N: int) -> str:
        # How to convert a number to base +2
        if N == 0: return "0"
        res = ''
        curr = 0
        while N != 0:
            curr = N % 2
            N = (N - curr) // (-2)
            res = str(curr) + res
        return res
```

With the bitwise operators (&, ^) in Python, the modular operation can be replaced by`N & 1`. Similarly, the update operation $N=(N-a[i])/b$ can be replaced by `N >> 1`

```Python
def baseNeg2(self, N: int) -> str:
        if N == 0 or N == 1: return str(N)
        
        return self.baseNeg2(-(N >> 1)) + str(N & 1)
```

### 877. Stone Game I

Always return true if the number of piles is even.

What if the number of piles is odd? 2d DP.

```python
def stoneGame(self, piles):
        """
        :type piles: List[int]
        :rtype: bool
        """
        n = len(piles)
        
        dp = [[0] * n for _ in range(n)]
        for i in range(n):
            dp[i][i] = piles[i]
        
        for step in range(1, n):
            for i in range(n-step):
                temp1 = piles[i] - dp[i+1][i+step]
                temp2 = piles[i+step] - dp[i][i+step-1]
                dp[i][i+step] = max(temp1, temp2)
        return dp[0][n-1] > 0
```

With 1d DP, we just need to overwrite the diagonal `dp[c][c]`.	Thus the space complexity is $O(N)$.

