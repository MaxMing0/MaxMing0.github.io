---
layout:     post
title:      LeetCode 1008 Construct Binary Search Tree from Preorder Traversal (Python)
number:     1008
level:      Medium
lcurl:      construct-binary-search-tree-from-preorder-traversal
youtube:    iLTP5J7bG14
bilibili1:  //player.bilibili.com/player.html?aid=752872033&bvid=BV1yk4y1R7oF&cid=180925894&page=1
xigua:      
date:       2020-04-26
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Tree
---

### 题目

Return the root node of a binary search tree that matches the given preorder traversal.

(Recall that a binary search tree is a binary tree where for every node, any descendant of node.left has a value < node.val, and any descendant of node.right has a value > node.val.  Also recall that a preorder traversal displays the value of the node first, then traverses node.left, then traverses node.right.)

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
    def bstFromPreorder(self, preorder: List[int]) -> TreeNode:
        def dfs(l, r):
            if l == r:
                return TreeNode(preorder[l])
            if l > r:
                return None
            val = preorder[l]
            node = TreeNode(val)
            pos = l + 1
            while pos < self.n and preorder[pos] < val:
                pos += 1
            node.left = dfs(l + 1, pos - 1)
            node.right = dfs(pos, r)
            return node
        
        self.n = len(preorder)
        return dfs(0, self.n - 1)
```