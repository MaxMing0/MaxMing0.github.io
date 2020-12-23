---
layout:     post
title:      LeetCode 110 Balanced Binary Tree (Python)
number:     110
level:      Medium
lcurl:      balanced-binary-tree
youtube:    g77qWrmnlAA
bilibili1:  //player.bilibili.com/player.html?aid=415812938&bvid=BV1sV411b7hR&cid=269987546&page=1
xigua:      
date:       2020-12-23
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - BST
    - DFS
---

### 题目

Given a binary tree, determine if it is height-balanced.

For this problem, a height-balanced binary tree is defined as:

  a binary tree in which the left and right subtrees of every node differ in height by no more than 1.

### 解题思路

递归，如果一个树是平衡的，那么两个子树也是平衡的，并且高度最多差1

### 代码
```python
class Solution:
    def isBalanced(self, root: TreeNode) -> bool:
        def dfs(root):
            if not root:
                return True, 0
            bl, hl = dfs(root.left)
            if not bl:
                return False, 0
            br, hr = dfs(root.right)
            if not br:
                return False, 0
            
            return abs(hl - hr) <= 1, max(hl, hr) + 1
        
        return dfs(root)[0]
```
