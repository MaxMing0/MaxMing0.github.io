---
layout:     post
title:      LeetCode 230 Kth Smallest Element in a BST (Python)
number:     230
level:      Medium
lcurl:      kth-smallest-element-in-a-bst
youtube:    60vz4CRfaxs
bilibili1:  //player.bilibili.com/player.html?aid=668135087&bvid=BV1ha4y1i7dZ&cid=193198118&page=1
xigua:      
date:       2020-05-20
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - BST
---

### 题目

Given a binary search tree, write a function kthSmallest to find the kth smallest element in it.

Note:

You may assume k is always valid, 1 ≤ k ≤ BST's total elements.

### 解题思路

一个BST的中序遍历就是将树中的所有节点排序，所有就返回中序遍历的第k个数，可以有递归和非递归两种做法

### 代码
```python
# 递归

class Solution:
    def kthSmallest(self, root: TreeNode, k: int) -> int:
        def inorder(root):
            if not root:
                return
            res = inorder(root.left)
            if res is not None:
                return res
            self.k -= 1
            if self.k == 0:
                return root.val
            else:
                return inorder(root.right)
            
        self.k = k
        return inorder(root)
```
```python
# 非递归

class Solution:
    def kthSmallest(self, root: TreeNode, k: int) -> int:
        stack = []
        while stack or root:
            while root:
                stack.append(root)
                root = root.left
            root = stack.pop()
            k -= 1
            if k == 0:
                return root.val
            root = root.right
```
