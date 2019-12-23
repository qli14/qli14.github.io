---
title: DFS and BFS
date: 2019-07-22 10:36:17
tags:
---

### Leetcode 429 N-ary tree level order traversal

Use an argument to track the level. If the level is out of the range, then append a new blank list to the result. (DFS)

```python
def levelOrder(self, root: 'Node') -> List[List[int]]:
        def recursion(node, level):
            if not node:
                return
            if level > len(res)-1: # a new level
                res.append([])
            res[level].append(node.val)
        
            for child in node.children:
                recursion(child, level+1)
                
        res = []
        recursion(root, 0)
        
        return res
```

A BFS method is to track the nodes of each level in a while loop.

```python
def levelOrder(self, root: 'Node') -> List[List[int]]:
        if not root: return []
        q = [root]
        res = []
        while q:
            res.append([node.val for node in q])
            # update q to the next level
            temp = []
            for node in q:
                for child in node.children:
                    if child:
                        temp.append(child)
            q = temp
            # Finally, q is tempy
        return res
```

