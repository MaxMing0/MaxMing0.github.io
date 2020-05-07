---
layout:     post
title:      LeetCode Cousins in Binary Tree (Python)
number:     9999
level:      na
lcurl:      
youtube:    2WbgNzAPZD4
bilibili1:  
xigua:      
date:       2020-05-07
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Tree
    - BFS
---

### 题目

In a binary tree, the root node is at depth 0, and children of each depth k node are at depth k+1.

Two nodes of a binary tree are cousins if they have the same depth, but have different parents.

We are given the root of a binary tree with unique values, and the values x and y of two different nodes in the tree.

Return true if and only if the nodes corresponding to the values x and y are cousins.

### 解题思路

使用BFS遍历树的每一层，将下一层所有结点放到一个set中，判断x和y是否同时出现在一层中，如果是返回True，只有一个出现返回False，都没有则继续下一层

### 代码
```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def isCousins(self, root: TreeNode, x: int, y: int) -> bool:
        if root.val == x or root.val == y:
            return False
        q = {root}
        while q:
            tmp = set()
            for node in q:
                if node.left and node.right:
                    if set([node.left.val, node.right.val]) == set([x, y]):
                        return False
                    tmp.add(node.left)
                    tmp.add(node.right)
                else:
                    tmp.add(node.left or node.right)
            q = {n for n in tmp if n is not None}
            values = {n.val for n in q}
            if x in values and y in values:
                return True
            if x in values or y in values:
                return False
        return False
```
