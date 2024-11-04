---
layout:     post
title:      LeetCode 314 Binary Tree Vertical Order Traversal (Python)
number:     314
level:      Medium
lcurl:      binary-tree-vertical-order-traversal
youtube:    
bilibili1:  
xigua:      
date:       2024-11-03
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - HashTable
---

### 题目

Given the root of a binary tree, return the vertical order traversal of its nodes' values. (i.e., from top to bottom, column by column).

If two nodes are in the same row and column, the order should be from left to right.

### 解题思路

按层进行bfs，bfs过程中记录遇到的最大和最小col，用一个字典存col相同的节点在值，最后按col从小到大输出结果

### 代码
```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def verticalOrder(self, root: Optional[TreeNode]) -> List[List[int]]:
        if not root:
            return []
        res = defaultdict(list)
        q = deque([(root, 0)])
        min_col = max_col = 0
        while q:
            node, col = q.popleft()
            res[col].append(node.val)
            if node.left:
                q.append((node.left, col - 1))
            if node.right:
                q.append((node.right, col + 1))
            min_col = min(min_col, col)
            max_col = max(max_col, col)
        return [res[i] for i in range(min_col, max_col + 1)]
```
