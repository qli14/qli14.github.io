---
title: Lowest Common Ancestor of Deepest Leaves
date: 2019-07-17 15:24:09
tags:
---

Solution by `lee215`
https://leetcode.com/problems/lowest-common-ancestor-of-deepest-leaves/discuss/334577/JavaC%2B%2BPython-Two-Recursive-Solution

```Python
def lcaDeepestLeaves(self, root):
        self.lca, self.deepest = None, 0
        def helper(node, depth):
            self.deepest = max(self.deepest, depth)
            if not node:
                return depth
            left = helper(node.left, depth + 1)
            right = helper(node.right, depth + 1)
            if left == right == self.deepest:
                self.lca = node
            return max(left, right)
        helper(root, 0)
        return self.lca
    '''
    Example: [1, 2, 3]
    helper([1, 2, 3], 0)
    	helper([2, 3], 1)
    		helper([], 2), left = 2
    		helper([], 2), right = 2
    		left = 2
    	helper([3], 1)
    		helper([], 2), left = 2
    		helper([], 2), right = 2
    		right = 2
    		
    Example: [1, 2, 3, 4]
    helper([1, 2, 3, 4], 0)
    	helper([2, 4], 1)
    		helper([4], 2)
    			helper([], 3), left = 3
    			helper([], 3), right = 3
    			left = 3
    		helper([], 2), right = 2
    		left = 3
    	helper([3], 1)
    		helper([], 2), left = 2
    		helper([], 2), right = 2
    		right = 2
        
    '''
```

