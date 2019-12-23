---
title: Smallest Sufficient Team
date: 2019-07-16 13:51:22
tags: Bit Manipulation, Dynamic Programming
---
Leetcode 1125, Smallest Sufficient Team

DP solution provided by `lee215`.
https://leetcode.com/problems/smallest-sufficient-team/discuss/334572/Python-DP-Solution

```python
def smallestSufficientTeam(self, req_skills, people):
        n, m = len(req_skills), len(people)
        key = {v: i for i, v in enumerate(req_skills)}
        dp = {0: []}
        for i, p in enumerate(people):
            # encode his skill with bit manipulation
            # 1010 means the position 1 and 3 in req_skills
            his_skill = 0
            for skill in p:
                if skill in key:
                    his_skill |= 1 << key[skill]
                    
            for skill_set, need in dp.items():
                # Example: skill_set 0010 his_skill 1010
                # skill_set | his_skill 1010
                # Intuitively, union of skill_set and his_skill
                with_him = skill_set | his_skill
                if with_him == skill_set: continue # his_skill is a subset of skill_set
                if with_him not in dp or len(dp[with_him]) > len(need) + 1:
                    dp[with_him] = need + [i]
        return dp[(1 << n) - 1]
```

