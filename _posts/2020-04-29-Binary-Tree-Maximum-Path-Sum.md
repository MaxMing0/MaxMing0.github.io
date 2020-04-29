---
layout:     post
title:      LeetCode 124 Binary Tree Maximum Path Sum (Python)
number:     124
level:      Hard
lcurl:      binary-tree-maximum-path-sum
youtube:    exLwDw6kPag
bilibili1:  //player.bilibili.com/player.html?aid=925425166&bvid=BV1CT4y1g7bR&cid=184750468&page=1
xigua:      
date:       2020-04-29
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Tree
    - DFS
---

### 题目

Given a non-empty binary tree, find the maximum path sum.

For this problem, a path is defined as any sequence of nodes from some starting node to any node in the tree along the parent-child connections. The path must contain at least one node and does not need to go through the root.

### 解题思路

递归，在递归到每个节点时，用经过该节点的最长路径和更新最终结果，为了两个子树中以子树根节点为起点的最长路径和的和加上自己，如果子树的和为负，则取0。并把当前节点的值加上最大子树的路径和（或0）返回给上一层，

### 代码
```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def maxPathSum(self, root: TreeNode) -> int:
        def traversal(root):
            if root is None:
                return 0
            left = max(0, traversal(root.left))
            right = max(0, traversal(root.right))
            self.res = max(self.res, left + right + root.val)
            return max(left, right, 0) + root.val

        self.res = float("-inf")
        traversal(root)
        return self.res
```
