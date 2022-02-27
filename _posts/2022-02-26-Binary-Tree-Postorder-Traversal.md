---
layout:     post
title:      LeetCode 145 Binary Tree Postorder Traversal (Python)
number:     145
level:      Easy
lcurl:      binary-tree-postorder-traversal
youtube:    QfG65IGqMs8
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

Given the root of a binary tree, return the postorder traversal of its nodes' values.

### 解题思路

递归和非递归两种方法

### 代码
```python
class Solution:
    def postorderTraversal(self, root: Optional[TreeNode]) -> List[int]:
        if not root:
             return []
        return self.postorderTraversal(root.left) + self.postorderTraversal(root.right) + [root.val]
```
```python
class Solution:
    def postorderTraversal(self, root: Optional[TreeNode]) -> List[int]:
        stack, res = [root], deque([])
        while stack:
            cur = stack.pop()
            if cur:
                res.appendleft(cur.val)
                stack.append(cur.left)
                stack.append(cur.right)
        return res
```
