---
title: Weekly Contest 152
date: 2019-09-01 16:51:23
tags:
description: Didn't participate in the contest. Did the virtual contest on Sunday. Solved the first two. TLE on the rest two.
---

### 1175. Prime Arrangements

Just need to count the number of primes with the Sieve of Eratosthenes.

### 1176. Diet Plan Performance

Use prefix sum to count the sum of every consecutive k days.

### 1177. Can Make Palindrom from Substring

Tried to count the frequency of each character in every given range, but TLE. 

A better method is the idea of prefix sum to count the frequency of chars.

```python
def canMakePaliQueries(self, s: str, queries: List[List[int]]) -> List[bool]:
        # Since substring can be rearranged, we only care about the frequency of each char.
        # length even. Then freq of every char is even. The number of chars with odd freq <= k * 2
        # length odd. One char with odd freq, other chars with even freq. The number of chars with odd freq <= k * 2 + 1
        #           Since the length is odd, there is at least one char with odd freq
        n = len(queries)
        res = [False] * n
        cnt = [[0] * 26]
        for i in range(len(s)):
            cnt.append(cnt[i][:])
            cnt[i + 1][ord(s[i]) - ord('a')] += 1
        # for i in range(len(s) + 1):
        #     print(cnt[i])
        for j in range(n):
            query = queries[j]
            
            odd = 0
            l = query[0]
            r = query[1]
            
            for k in range(26):
                if ( cnt[r + 1][k] - cnt[l][k] ) % 2 == 1:
                    odd += 1

            # print(odd)
            
            if (query[1] - query[0] + 1) % 2 == 0 and odd <= 2 * query[2]:
                res[j] = True
                continue
            if (query[1] - query[0] + 1) % 2 == 1 and odd <= 2 * query[2] + 1:
                res[j] = True    
        
        return res
```

### 1188. Number of Valid Words for Each Puzzle

TLE with brute force method.