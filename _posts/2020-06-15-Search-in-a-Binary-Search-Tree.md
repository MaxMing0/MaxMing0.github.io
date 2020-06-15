---
layout:     post
title:      LeetCode 700 Search in a Binary Search Tree (Python)
number:     700
level:      Easy
lcurl:      search-in-a-binary-search-tree
youtube:    e-Nqe86fumI
bilibili1:  //player.bilibili.com/player.html?aid=201075694&bvid=BV14z411e76U&cid=202279311&page=1
xigua:      
date:       2020-06-15
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - BST
---

### 题目

Given the root node of a binary search tree (BST) and a value. You need to find the node in the BST that the node's value equals the given value. Return the subtree rooted with that node. If such node doesn't exist, you should return NULL.

### 解题思路

递归和非递归两种做法，如果当前节点的值为要找的值则返回，大于则在左子树，小于在右子树

### 代码
非递归
```python
class Solution:
    def searchBST(self, root: TreeNode, val: int) -> TreeNode:
        if not root:
            return None
        while root:
            if root.val == val:
                return root
            if root.val > val:
                root = root.left
            else:
                root = root.right
```
递归
```python
class Solution:
    def searchBST(self, root: TreeNode, val: int) -> TreeNode:
        if not root:
            return None
        if root.val == val:
            return root
        if root.val > val:
            return self.searchBST(root.left, val)
        return self.searchBST(root.right, val)
```
