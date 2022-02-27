---
layout:     post
title:      LeetCode 94 Binary Tree Inorder Traversal (Python)
number:     94
level:      Easy
lcurl:      binary-tree-inorder-traversal
youtube:    M2L5XiBkH28
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

Given the root of a binary tree, return the inorder traversal of its nodes' values.

### 解题思路

递归和非递归两种方法

### 代码
```python
class Solution:
    def inorderTraversal(self, root: Optional[TreeNode]) -> List[int]:
        if not root:
             return []
        return self.inorderTraversal(root.left) + [root.val] + self.inorderTraversal(root.right)
```
```
class Solution:
    def inorderTraversal(self, root: Optional[TreeNode]) -> List[int]:
        stack, res = [], []   
        cur = root
        while cur or stack:
            while cur:
                stack.append(cur)
                cur = cur.left
            node = stack.pop()
            res.append(node.val)
            cur = node.right
        return res
```
