---
layout:     post
title:      LeetCode 1448 Count Good Nodes in Binary Tree (Python)
number:     1448
level:      Medium
lcurl:      count-good-nodes-in-binary-tree
youtube:    JI4OPKSu7f4
bilibili1:  //player.bilibili.com/player.html?aid=838135824&bvid=BV1Zg4y1q7kc&cid=191917571&page=1
xigua:      
date:       2020-05-16
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Tree
    - DFS
---

### 题目

Given a binary tree root, a node X in the tree is named good if in the path from root to X there are no nodes with a value greater than X.

Return the number of good nodes in the binary tree.

### 解题思路

DFS，每次将路径上的最大值传给下一层，并把左右子树的结果以及当前节点是否符合条件求出总和，返回给上一层

### 代码
```python
class Solution:
    def goodNodes(self, root: TreeNode) -> int:
        def dfs(root, max_val):
            res = int(root.val >= max_val)
            if root.left:
                res += dfs(root.left, max(max_val, root.val))
            if root.right:
                res += dfs(root.right, max(max_val, root.val))
            return res
        
        return dfs(root, -10000)
```
