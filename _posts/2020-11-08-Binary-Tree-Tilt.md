---
layout:     post
title:      LeetCode 563 Binary Tree Tilt (Python)
number:     563
level:      Easy
lcurl:      binary-tree-tilt
youtube:    dhzGRyVherc
bilibili1:  //player.bilibili.com/player.html?aid=415202128&bvid=BV1KV41117ho&cid=253818252&page=1
xigua:      
date:       2020-11-08
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Tree
    - DFS
---

### 题目

Given the root of a binary tree, return the sum of every tree node's tilt.

The tilt of a tree node is the absolute difference between the sum of all left subtree node values and all right subtree node values. If a node does not have a left child, then the sum of the left subtree node values is treated as 0. The rule is similar if there the node does not have a right child.

### 解题思路

递归，对于每个节点，求出左右两个子树之和，将差的绝对值加到结果里，然后将两个子树之和加本身，返回给上一层

### 代码
```python
class Solution:
    def findTilt(self, root: TreeNode) -> int:
        def dfs(root):
            if not root:
                return 0
            left = dfs(root.left)
            right = dfs(root.right)
            self.res += abs(left - right)
            return left + right + root.val
        
        self.res = 0
        dfs(root)
        return self.res
```
