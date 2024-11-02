---
layout:     post
title:      LeetCode 1609 Even Odd Tree (Python)
number:     1609
level:      Medium
lcurl:      even-odd-tree
youtube:    
bilibili1:  
xigua:      
date:       2024-11-01
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - BFS
---

### 题目

A binary tree is named Even-Odd if it meets the following conditions:

The root of the binary tree is at level index 0, its children are at level index 1, their children are at level index 2, etc.
- For every even-indexed level, all nodes at the level have odd integer values in strictly increasing order (from left to right).
- For every odd-indexed level, all nodes at the level have even integer values in strictly decreasing order (from left to right).
Given the root of a binary tree, return true if the binary tree is Even-Odd, otherwise return false.

### 解题思路

按层进行bfs，把每层的值存在一个数组里进行判断，是否全为奇/偶数，递增/递减

### 代码
```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def isEvenOddTree(self, root: Optional[TreeNode]) -> bool:
        def is_increase(q, is_even):
            if is_even:
                if q[0].val % 2 == 0:
                    return False
                for i in range(1, len(q)):
                    if q[i].val % 2 == 0:
                        return False
                    if q[i].val <= q[i - 1].val:
                        return False
            else:
                if q[0].val % 2 != 0:
                    return False
                for i in range(1, len(q)):
                    if q[i].val % 2 != 0:
                        return False
                    if q[i].val >= q[i - 1].val:
                        return False
            return True

        is_even = True
        q = [root]
        while q:
            if not is_increase(q, is_even):
                return False
            tmp = []
            for n in q:
                if n.left:
                    tmp.append(n.left)
                if n.right:
                    tmp.append(n.right)
            q = tmp[:]
            is_even = not is_even
        return True

```
