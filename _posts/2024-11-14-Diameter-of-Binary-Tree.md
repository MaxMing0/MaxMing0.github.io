---
layout:     post
title:      LeetCode 543 Diameter of Binary Tree (Python)
number:     543
level:      Easy
lcurl:      diameter-of-binary-tree
youtube:    
bilibili1:  
xigua:      
date:       2024-11-14
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - DFS
---

### 题目

Given the root of a binary tree, return the length of the diameter of the tree.

The diameter of a binary tree is the length of the longest path between any two nodes in a tree. This path may or may not pass through the root.

The length of a path between two nodes is represented by the number of edges between them.

### 解题思路

dfs求两个子树的深度，直径为两个子树的深度和

### 代码
```python
class Solution:
    def diameterOfBinaryTree(self, root: Optional[TreeNode]) -> int:
        def dfs(root):
            l = r = 0
            if root.left:
                l = dfs(root.left)
            if root.right:
                r = dfs(root.right)
            self.res = max(self.res, l + r + 1)
            return max(l, r) + 1

        self.res = 0
        dfs(root)
        return self.res - 1
```
