---
title: Weekly Contest 151
date: 2019-08-25 13:49:45
tags:
description: Solved the first two, had no idea on the third one, and TLE on the last one.
---

### 1169. Invalid Transactions

Just use a dictionary to store the transaction under the same name.

```python
 def invalidTransactions(self, transactions):
        """
        :type transactions: List[str]
        :rtype: List[str]
        """
        res = []
        dict1 = {}
        for trans in transactions:
            # print(dict1)
            name, time, amount, city = trans.split(',')
            if int(amount) > 1000:
                res.append(trans)
            if name not in dict1:
                dict1[name] = ([time], [amount], [city], [trans])
            else:
                for i in range(len(dict1[name][0])):
                    if city != dict1[name][2][i] and abs(int(time) - int(dict1[name][0][i])) <= 60:
                        if int(amount) <= 1000 and trans not in res: res.append(trans) 
                            # why checking trans not in res
                        	# Necessay since the current trans could have been 
                            # saved in dict1 with another previous conflict trans 
                        if int(dict1[name][1][i]) <= 1000 and dict1[name][3][i] not in res: res.append(dict1[name][3][i])
                dict1[name][0].append(time)
                dict1[name][1].append(amount)
                dict1[name][2].append(city)
                dict1[name][3].append(trans)
        return res
```

### 1170. Compare strings by frequency of the smallest character

Trivial

### 1171. Remove zero sum consecutive nodes from linked list

Had no idea during the contest. 

[Lee215 solution.](https://leetcode.com/problems/remove-zero-sum-consecutive-nodes-from-linked-list/discuss/366319/JavaC%2B%2BPython-Greedily-Skip-with-HashMap) 

The key idea is to calculate the summation up to the current node. The consecutive sum between two nodes can be calculated from the difference between the corresponding two sums.

```python
def removeZeroSumSublists(self, head):
        """
        :type head: ListNode
        :rtype: ListNode
        """
        dummy = ListNode(0)
        dummy.next = head
        curr = head
        dict1 = {0: dummy}
        presum = 0
        
        while curr:
            presum += curr.val
            if presum not in dict1:
                dict1[presum] = curr
            else:
                dict1[presum].next = curr.next
            
            curr = curr.next
        return dummy.next
```

### 1172. Dinner plate stacks

TLE during the contest since the position to push is searched with a loop.

The key idea is to use a heap to mark the available stacks to push.

```python
class DinnerPlates(object):

    def __init__(self, capacity):
        """
        :type capacity: int
        """
        self.stacks = [[]]
        self.capacity = capacity

    def push(self, val):
        """
        :type val: int
        :rtype: None
        """
        if len(self.stacks[-1]) == self.capacity:
            self.stacks.append([])
        for i in range(len(self.stacks)):
            # stack = self.stacks[i]
            if len(self.stacks[i]) < self.capacity:
                # stack.append(val)
                self.stacks[i].append(val) # = stack
                break
        # self.stacks[-1].append(val)
        # print(self.stacks)

    def pop(self):
        """
        :rtype: int
        """
        res = -1
        if not self.stacks: return res
        if len(self.stacks[-1]) == 1:
            # res = self.stacks[-1].pop()
            # print(self.stacks)
            res = self.stacks.pop()[0]
            # print(self.stacks)
        else:
            res = self.stacks[-1].pop()
        return res
            

    def popAtStack(self, index):
        """
        :type index: int
        :rtype: int
        """
        if index >= len(self.stacks): return -1
        stack = self.stacks[index]
        if not stack: return -1
        res = stack.pop()
        self.stacks[index] = stack
        return res
```



