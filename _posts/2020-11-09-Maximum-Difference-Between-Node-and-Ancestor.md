---
layout:     post
title:      LeetCode 1026 Maximum Difference Between Node and Ancestor (Python)
number:     1026
level:      Medium
lcurl:      maximum-difference-between-node-and-ancestor
youtube:    JCeKw2deBjo
bilibili1:  //player.bilibili.com/player.html?aid=542668927&bvid=BV1fi4y157ZS&cid=254156199&page=1
xigua:      
date:       2020-11-09
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Tree
    - DFS
---

### 题目

Given the root of a binary tree, find the maximum value V for which there exist different nodes A and B where V = |A.val - B.val| and A is an ancestor of B.

A node A is an ancestor of B if either: any child of A is equal to B, or any child of A is an ancestor of B.

### 解题思路

递归，每次向下传递当前路径上的最大值和最小值（因为为了差最大，不会是中间的节点），然后与当前的值做差，更新结果

### 代码
```python
class Solution:
    def maxAncestorDiff(self, root: TreeNode) -> int:
        def dfs(root, max_val, min_val):
            tmp = max(abs(root.val - max_val), abs(root.val - min_val))
            self.res = max(self.res, tmp)
            max_val = max(max_val, root.val)
            min_val = min(min_val, root.val)
            if root.left:
                dfs(root.left, max_val, min_val)
            if root.right:
                dfs(root.right, max_val, min_val)
        
        self.res = 0
        dfs(root, root.val, root.val)
        return self.res
```
