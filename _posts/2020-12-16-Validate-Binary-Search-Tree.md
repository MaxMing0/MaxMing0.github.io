---
layout:     post
title:      LeetCode 98 Validate Binary Search Tree (Python)
number:     98
level:      Medium
lcurl:      validate-binary-search-tree
youtube:    3HZtiZmidHs
bilibili1:  //player.bilibili.com/player.html?aid=245685047&bvid=BV1Hv411478d&cid=267358661&page=1
xigua:      
date:       2020-12-16
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - BST
---

### 题目

Given the root of a binary tree, determine if it is a valid binary search tree (BST).

A valid BST is defined as follows:

- The left subtree of a node contains only nodes with keys less than the node's key.
- The right subtree of a node contains only nodes with keys greater than the node's key.
- Both the left and right subtrees must also be binary search trees.

### 解题思路

使用DFS遍历树，遍历的时候向下传上下界，根据上下界判断是否符合要求

### 代码
```python
class Solution:
    def isValidBST(self, root: TreeNode) -> bool:
        def check(root, l, r):
            if root == None:
                return True
            val = root.val
            if val <= l or val >= r:
                return False
            return check(root.left, l, val) and check(root.right, val, r)
        return check(root, float('-inf'), float('inf'))
```
