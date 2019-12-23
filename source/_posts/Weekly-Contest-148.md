---
title: Weekly-Contest-148
date: 2019-08-03 23:01:40
tags:
description: Forgot this contest and joined when only 10 mins left. Solved the first problem. Then tried to solve the rest 3 within one hour.
---

### Decrease Elements To Make Array Zigzag

Just code.

### Binary Tree Coloring Game

Count the number of nodes in three directions: left and right child, parent.

```python
def btreeGameWinningMove(self, root, n, x):
        """
        :type root: TreeNode
        :type n: int
        :type x: int
        :rtype: bool
        """
        # find the node with node.val == x
        # find the number of nodes with root of node.left, node.right
        # and the other child of node's parent + 1 (the parent itself)
        
        # From the three directions, find the max. number of nodes. 
        # Win if num. > n / 2
        
        # Only need to calcualte # of nodes with root of node.left and node.right
        # The number of node in the third direction is n - (# node.left) - (# node.right) - 1
        result = [0, 0]
        def dfs(node):
            if not node: return 0
            if node.val == x:
                result[0], result[1] = dfs(node.left), dfs(node.right)
                # if I write
                # result = [dfs(node.left), dfs(node.right)]
                # then
                # result is just a local variable
            return dfs(node.left) + dfs(node.right) + 1
        
        dfs(root)
        # print(result)
        return max(result[0], result[1], n - result[0] - result[1] - 1) > n /2
```



### Snapshot Array

Tried to store the whole array in every snapshot, but MLE (memory limit exceeded).

Actually, it's not necessary to store the whole array since most of them are just zero. Instead, just use a dictionary to store the index and value.

### Longest Chunked Palindrome Decomposition

Just go through the string. How about the dp solution?

```python
def longestDecomposition(self, text):
        """
        :type text: str
        :rtype: int
        """
        result = 0
        i = 0
        j = 0
        n = len(text)
        
        while i < n:
            while j < n and text[i:j+1] != text[n-(j+1):n-i]:
                j += 1
            i = j + 1
            j = i
            result += 1
        return result
```

