---
layout:     post
title:      LeetCode 783 Minimum Distance Between BST Nodes (Python)
number:     783
level:      Easy
lcurl:      minimum-distance-between-bst-nodes
youtube:    yrVwMZmUQbg
bilibili1:  
xigua:      
date:       2023-02-16
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - BST
---

### 题目

Given the root of a Binary Search Tree (BST), return the minimum difference between the values of any two different nodes in the tree.

### 解题思路

对树进行中序遍历，因为中序遍历是有序的，所以遍历的时候和前一个遍历到的值作差，并更新结果

### 代码
```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    res = 100000
    pre = -1
    def minDiffInBST(self, root: Optional[TreeNode]) -> int:
        def inorder(node):
            if node.left:
                inorder(node.left)
            if self.pre >= 0:
                self.res = min(self.res, node.val - self.pre)
            self.pre = node.val
            if node.right:
                inorder(node.right)

        inorder(root)
        return self.res
```
