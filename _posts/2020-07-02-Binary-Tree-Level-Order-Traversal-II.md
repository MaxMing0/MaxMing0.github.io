---
layout:     post
title:      LeetCode 107 Binary Tree Level Order Traversal II (Python)
number:     107
level:      Easy
lcurl:      binary-tree-level-order-traversal-ii
youtube:    ZIWcvjXXAMw
bilibili1:  //player.bilibili.com/player.html?aid=498646092&bvid=BV1yK411n76R&cid=208053435&page=1
xigua:      
date:       2020-07-02
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - BFS
---

### 题目

Given a binary tree, return the bottom-up level order traversal of its nodes' values. (ie, from left to right, level by level from leaf to root).

### 解题思路

从根节点开始dfs，把每一层放到结果里，同时求出下一层的所有节点

### 代码
```python
class Solution:
    def levelOrderBottom(self, root: TreeNode) -> List[List[int]]:
        if not root:
            return None
        res, q = [], [root]
        while q:
            val, tmp = [], []
            for node in q:
                val.append(node.val)
                if node.left:
                    tmp.append(node.left)
                if node.right:
                    tmp.append(node.right)
            res.append(val)
            q = tmp
        return res[::-1]
```
