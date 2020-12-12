---
layout:     post
title:      LeetCode 865 Smallest Subtree with all the Deepest Nodes (Python)
number:     865
level:      Medium
lcurl:      smallest-subtree-with-all-the-deepest-nodes
youtube:    CVLuS92R_os
bilibili1:  //player.bilibili.com/player.html?aid=415506728&bvid=BV1CV41187ZA&cid=265790858&page=1
xigua:      
date:       2020-12-12
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - DFS
    - Tree
---

### 题目

Given the root of a binary tree, the depth of each node is the shortest distance to the root.

Return the smallest subtree such that it contains all the deepest nodes in the original tree.

A node is called the deepest if it has the largest depth possible among any node in the entire tree.

The subtree of a node is tree consisting of that node, plus the set of all descendants of that node.

Note: This question is the same as 1123: https://leetcode.com/problems/lowest-common-ancestor-of-deepest-leaves/

### 解题思路

dfs，返回当前子树的哪个最深节点包含所有叶节点以及该子树的高度，如果两个子树高度相同，返回跟节点，否则返回较深子树的结果

### 代码
```python
class Solution:
    def subtreeWithAllDeepest(self, root: TreeNode) -> TreeNode:
        def dfs(root):
            if not root:
                return (None, 0)
            l = dfs(root.left)
            r = dfs(root.right)
            depth = max(l[1], r[1]) + 1
            if l[1] < r[1]:
                return (r[0], depth)
            elif l[1] > r[1]:
                return (l[0], depth)
            return (root, depth)

        return dfs(root)[0]
```
