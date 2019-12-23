---
title: 883 Max consecutive ones II
date: 2019-10-17 15:41:19
tags:
---

Prefix sum.

A better solution is finding the longest subarray with at most one 0.

```python
def findMaxConsecutiveOnes(self, nums: List[int]) -> int:
        # 883. Flip at most one 0
        # if nums[i] == 0 and it's flipped, the max consecutive ones is
        #   1 + end[i - 1] + start[i + 1]
        count = 0
        res = 0
        n = len(nums)
        
        # start[i] consecutive ones starting from i
        # end[i] consecutive ones ending in i
        start = [0] * n
        end = [0] * n
        
        if nums[-1] == 1:
            start[-1] = 1
        for i in range(n - 2, -1, -1):
            if nums[i] == 1:
                start[i] = 1 + start[i + 1]
                
        if nums[0] == 1:
            end[0] = 1
        for i in range(1, n):
            if nums[i] == 1:
                end[i] = 1 + end[i - 1]
        
        # print(start, end)
        for i in range(n):
            if nums[i] == 0:
                res = max(res, count)
                count = 0
                
                flip = 1
                if i - 1 >= 0:
                    flip += end[i - 1]
                if i + 1 < n:
                    flip += start[i + 1]
                # print(i, flip)
                res = max(res, flip)
                
            else:
                count += 1
        return res
```

