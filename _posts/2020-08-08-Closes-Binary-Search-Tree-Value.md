---
layout:     post
title:      LeetCode 270 Closest Binary Search Tree Value (Python)
number:     270
level:      Easy
lcurl:      closest-binary-search-tree-value
youtube:    Y5ga1T04UNA
bilibili1:  //player.bilibili.com/player.html?aid=541655843&bvid=BV1fi4y1u7Sb&cid=222001433&page=1
xigua:      
date:       2020-08-08
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - BST
---

### 题目

Given a non-empty binary search tree and a target value, find the value in the BST that is closest to the target.

Note:
- Given target value is a floating point.
- You are guaranteed to have only one unique value in the BST that is closest to the target.

### 解题思路

从根开始和目标值进行比较，如果目标值小于当前节点，向左遍历，否则向右遍历

### 代码
```python
class Solution:
    def closestValue(self, root: TreeNode, target: float) -> int:
        res = root.val
        while root:
            res = min(res, root.val, key = lambda x: abs(target - x))
            root = root.left if target < root.val else root.right
        return res
```
