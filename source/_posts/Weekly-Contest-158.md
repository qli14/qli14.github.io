---
title: Weekly Contest 158
date: 2019-10-13 10:08:12
tags:
description: Solved the first three problems. Not enough time for the last one. Later solved the last one. No as difficult as expected, altough it's marked as hard. No special algorithms involved.
---

### 1221. Split a string in balanced strings

Running count

### 1222. Queens that can attack the king

Search from the King or search along the queens and keep the closest ones along each direction

### 5224 Dice roll simulation

Feels like a dp problem. It takes almost one hour, but finally AC.

(10/22/2019) Revisited this problem with a dp method. Much faster.

```python
class Solution:
    def dieSimulator(self, n: int, rollMax: List[int]) -> int:
        # dp[i][j] the number of valid sequences ending with (j + 1) with (i + 1) rolls
        dp = [[0] * 7 for _ in range(n)]
        # here dp[i][6] store the sum of dp[i][0-5]
        
        for j in range(6):
            dp[0][j] = 1
        dp[0][6] = 6
        
        for i in range(1, n):
            temp = 0  # store the sum of dp[i][*]
            for j in range(6):
                # update dp[i][j], then remove the illegal seqs.
                dp[i][j] = dp[i - 1][6]
                
                # if (i + 1) <= rollMax[j]
                # no worry about illegal seqs.
                if i == rollMax[j]:
                    # only one illegal, all -j-
                    dp[i][j] -= 1
                elif i > rollMax[j]:
                    # we choose j at index i
                    # to make [0, i] illegal
                    # we must have at least rollMax[j] + 1 concecutive -j-
                    
                    # in [0, i - 1], we can't have more than rollMax[j]
                    # since [0, i - 1] must form a valid sequence
                    
                    # THUS, we must have exactly rollMax[j] concecutive -j- 
                    # in [0, i - 1], ending in (i - 1)
                    # define pree = i - rollMax - 1
                    # the elements in range(pre, i) must be set to j
                    # then at index pre, we can't choose j, otherwise,
                    # we have rollMax[j] + 1 concecutive -j-
                    # in the range[prev, i - 1]
                    prev = i - rollMax[j] - 1
                    dp[i][j] -= dp[prev][6] - dp[prev][j]
                temp += dp[i][j] % (10 ** 9 + 7)
            dp[i][6] = temp % (10 ** 9 + 7)
        return dp[-1][6]
```



### 1225. Maximum equal frequency

Use two dictionaries to count the frequency of each number and the frequency of each frequency.

Need to delete the elements with zero frequency.