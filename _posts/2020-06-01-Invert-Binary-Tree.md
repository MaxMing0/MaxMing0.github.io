---
layout:     post
title:      LeetCode 226 Invert Binary Tree (Python)
number:     226
level:      Easy
lcurl:      invert-binary-tree
youtube:    f0_3O1msz4I
bilibili1:  //player.bilibili.com/player.html?aid=498400336&bvid=BV1FK411p7Co&cid=197542459&page=1
xigua:      
date:       2020-06-01
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Tree
    - Recursion
---

### 题目

Invert a binary tree.

### 解题思路

使用递归的方法，假设子树已经操作完成，交换左右子树

### 代码
```python
class Solution:
    def invertTree(self, root: TreeNode) -> TreeNode:
        if root:
            root.left, root.right = self.invertTree(root.right), self.invertTree(root.left)
        return root
```
