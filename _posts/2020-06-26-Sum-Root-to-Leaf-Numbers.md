---
layout:     post
title:      LeetCode 129 Sum Root to Leaf Numbers (Python)
number:     129
level:      Medium
lcurl:      sum-root-to-leaf-numbers
youtube:    FQnL0MmjErA
bilibili1:  //player.bilibili.com/player.html?aid=498739419&bvid=BV1VK411H7o5&cid=206008483&page=1
xigua:      
date:       2020-06-26
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - DFS
---

### 题目

Given a binary tree containing digits from 0-9 only, each root-to-leaf path could represent a number.

An example is the root-to-leaf path 1->2->3 which represents the number 123.

Find the total sum of all root-to-leaf numbers.

### 解题思路

递归向下传递当前路径的数，如果是叶节点，返回这个数，否则返回两个子树和

### 代码
```python
class Solution:
    def sumNumbers(self, root: TreeNode) -> int:
        def find(root, n):
            if root is None:
                return 0
            cur = n * 10 + root.val
            if root.left is None and root.right is None:
                return cur
            return find(root.left, cur) + find(root.right, cur)
        
        return find(root, 0)
```
