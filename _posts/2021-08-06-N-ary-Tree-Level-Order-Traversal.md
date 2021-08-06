---
layout:     post
title:      LeetCode 429 N-ary Tree Level Order Traversal (Python)
number:     429
level:      Medium
lcurl:      n-ary-tree-level-order-traversal
youtube:    7wBP03UoubU
bilibili1:  //player.bilibili.com/player.html?aid=249697109&bvid=BV1Uv411K77M&cid=384023161&page=1
xigua:      
date:       2021-08-06
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - BFS
---

### 题目

Given an n-ary tree, return the level order traversal of its nodes' values.

Nary-Tree input serialization is represented in their level order traversal, each group of children is separated by the null value (See examples).

### 解题思路

从根开始按层进行BFS遍历，把每层的数值存到结果里

### 代码
```python
class Solution:
    def levelOrder(self, root: 'Node') -> List[List[int]]:
        if not root:
            return []
        q = [root]
        res = []
        while q:
            res.append([])
            next_level = []
            for node in q:
                res[-1].append(node.val)
                for child in node.children:
                    next_level.append(child)
            q = next_level
        return res      
```
