---
layout:     post
title:      LeetCode 404 Sum of Left Leaves (Python)
number:     404
level:      Easy
lcurl:      sum-of-left-leaves
youtube:    E_fab7lAKR4
bilibili1:  
xigua:      
date:       2020-08-24
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Tree
---

### 题目

Find the sum of all left leaves in a given binary tree.

### 解题思路

递归，递归的时候传一个标记，是左子树还是右子树

### 代码
```python
class Solution:
    def sumOfLeftLeaves(self, root: TreeNode) -> int:
        def sumOfLeft(root, flag):
            if not root:
                return 0
            if flag and not root.left and not root.right:
                return root.val
            return sumOfLeft(root.left, True) + sumOfLeft(root.right, False)
        
        return sumOfLeft(root, False)
```
