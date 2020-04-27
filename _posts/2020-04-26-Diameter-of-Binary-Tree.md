---
layout:     post
title:      LeetCode 543 Diameter of Binary Tree (Python)
number:     543
level:      Easy
lcurl:      diameter-of-binary-tree
youtube:    pGMRZ_lglio
bilibili1:  //player.bilibili.com/player.html?aid=882708790&bvid=BV12K4y1r78T&cid=176918095&page=1
xigua:      
date:       2020-04-26
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Tree
---

### 题目

Given a binary tree, you need to compute the length of the diameter of the tree. The diameter of a binary tree is the length of the longest path between any two nodes in a tree. This path may or may not pass through the root.

### 解题思路



### 代码
```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    res = 0
    def diameterOfBinaryTree(self, root: TreeNode) -> int:
        def dfs(root):
            if not root:
                return 0
            l = dfs(root.left)
            r = dfs(root.right)
            self.res = max(self.res, l + r)
            return max(l, r) + 1
        
        if not root:
            return 0
        dfs(root)
        return self.res
```