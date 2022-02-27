---
layout:     post
title:      LeetCode 144 Binary Tree Preorder Traversal (Python)
number:     144
level:      Easy
lcurl:      binary-tree-preorder-traversal
youtube:    ZDwgCSTRRiQ
bilibili1:  
xigua:      
date:       2022-02-26
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Tree
---

### 题目

Given the root of a binary tree, return the preorder traversal of its nodes' values.

### 解题思路

递归和非递归两种方法

### 代码
```python
class Solution:
    def preorderTraversal(self, root: Optional[TreeNode]) -> List[int]:
        if not root:
             return []
        return [root.val] + self.preorderTraversal(root.left) + self.preorderTraversal(root.right)
```
```python
class Solution:
    def preorderTraversal(self, root: Optional[TreeNode]) -> List[int]:
        stack, res = [root], []   
        while stack:
            cur = stack.pop()
            if cur:
                res.append(cur.val)
                stack.append(cur.right)
                stack.append(cur.left)
        return res
```
