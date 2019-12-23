---
title: Weekly Contest 160
date: 2019-10-28 16:42:39
tags:
description: Solved only the first one.
---

### 1237. Find Positive Integer Solution for a Given Equation 

Binary search. This is the only one I solved during the contest

###  1238. Circular Permutation in Binary Representation 

During the contest, I used back tracking but got wrong answer. The problem is that the permutation must be circular. Later it turns out the back tracking renders TLE.

The standard solution should be using gray code.

The interesting observation is that the n-bit gray code can be induced from (n-1)-bit  binary code.

###  1239. Maximum Length of a Concatenated String with Unique Characters 

Back tracking. 

Bit-mask by [huahua](https://www.youtube.com/watch?v=N7womGmLXh8) for state compression.

Bitwise-and `&`, bitwise-or `|`.

It doesn't help in my implementation. The runtime becomes longer, 220 ms compared with 144 ms with back tracking. Anyway, it's good to know about the state compression with bitwise operators.

```python
def maxLength(self, arr: List[str]) -> int:
        # time complexity 2 ^ n
        # n is the length of arr
        # find all the subsets that meet the requirements, i.e. no common characters
        # then return the max length
        
        # back tracking
        # keep the curr concatenated string
        def countOnes(n):
            if n == 0: return 0
            count = 0
            while n > 0:
                if n % 2 != 0:
                    count += 1
                n = n >> 1
            return count
        def backTrack(i, curr):
            if i == len(a):
                self.res = max(self.res, countOnes(curr))
                return
    
            if a[i] & curr == 0: # no duplicates
                backTrack(i + 1, curr | a[i])
                
            backTrack(i + 1, curr)
        
        self.res = 0
        a = []
        # convert all string to binary representations
        for s in arr:
            if len(set(s)) != len(s):
                continue
            temp = 0
            for c in s:
                temp += 1 << (ord(c) - ord('a'))
            a.append(temp)
                
        
        backTrack(0, 0)
        return self.res
```



###  1240. Tiling a Rectangle with the Fewest Squares 

Too difficult

