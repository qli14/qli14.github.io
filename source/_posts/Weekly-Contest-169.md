---
title: Weekly Contest 169
date: 2019-12-28 22:29:57
tags: Leetcode
description: (3/4 16.6%) I had around one hour for the last problem. Worked out a back tracking solution, but TLE. Later I realized that the assignment of letters should be from least significant digits to the most significant digits. If the digits in the left and right hand side don't match, there is not poiting in going forward.
mathjax: true
---

### 1307. Verbal arithmetic puzzle

During the contest, I tried a brute-force back-tracking for all possible combinations, but TLE. The time complexity is $O(n!)$, where $n$ is the number of distinct characters. 

Later, I found a nice solution by [li-_-il](https://leetcode.com/problems/verbal-arithmetic-puzzle/discuss/463886/python-backtracking-efficient-column-wise-w-explanation/417569). The idea is following the addition in the vertical form. Starting from the least significant bit (LSB), try the assignment of each letter in each word and calculate the remainder and carry in the current digit. Compare the remainder with the value of the current digit in result. If the remainder has been assigned to other letters or the current digit in result has been assigned to other values, it's impossible to find a valid solution. Otherwise, assign the remainder to the current digit in result and continue.

This method is kind of like a 2D version of back tracking. The other trick I learned about is the un-assignment during back tracking. I used this trick to improve the performance of LC 1284 (Minimum number of flips to convert binary matrix to zero matrix). The runtime was reduced by half. 

```python
class Solution:
    def isSolvable(self, words: List[str], result: str) -> bool:
        n = 0
        for i in range(len(words)):
            n = max(n, len(words[i]))
            words[i] = words[i][::-1]
        if n > len(result): # at least one of words is longer than result. 
            return False 
        
        result = result[::-1]
        assign = {}
        
        def solve(i, j, carry):
            if j == len(words): # column i is over
                curr_col_sum = carry
                for word in words:
                    if i < len(word):
                        curr_col_sum += assign[word[i]]
                # compare with result[i]
                if result[i] in assign:
                    if curr_col_sum % 10 != assign[result[i]]:
                        return False
                    else:
                        return solve(i + 1, 0, curr_col_sum // 10)
                else:
                    if curr_col_sum % 10 in assign.values():
                        return False
                    if curr_col_sum % 10 == 0 and i == len(result) - 1:
                        return False
                    assign[result[i]] = curr_col_sum % 10
                    res = solve(i + 1, 0, curr_col_sum // 10)
                    del assign[result[i]]
                    return res
            if i == len(result): # all columns are over, len(result) >= n
                return carry == 0
            
            if i >= len(words[j]) or words[j][i] in assign:
                return solve(i, j + 1, carry)
            else:
                for val in range(10):
                    if val == 0 and i == len(words[j]) - 1: # leading digit of words[j]
                        continue
                    if val not in assign.values():
                        assign[words[j][i]] = val
                        res = solve(i, j + 1, carry)
                        if res: return True # don't understand this line
                        # once a solution is found, return True
                        del assign[words[j][i]]
                return False 
            	# tried all possible values for words[j][i] but none of them works
        return solve(0, 0, 0)
        # follow-up: How to find all the possible solutions?
```
