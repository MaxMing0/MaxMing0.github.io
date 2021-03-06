---
layout:     post
title:      LeetCode 637 Average of Levels in Binary Tree (Python)
number:     637
level:      Easy
lcurl:      average-of-levels-in-binary-tree
youtube:    y0vtWdlVWhA
bilibili1:  //player.bilibili.com/player.html?aid=629610265&bvid=BV1eb4y1976M&cid=306990140&page=1
xigua:      
date:       2021-03-06
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Tree
    - BFS
---

### 题目

Given a non-empty binary tree, return the average value of the nodes on each level in the form of an array.

### 解题思路

从根开始一层一层bfs，遍历的时候求出每层的平均值

### 代码
```python
class Solution:
    def averageOfLevels(self, root: TreeNode) -> List[float]:
        res = []
        q = [root]
        while q:
            tmp = []
            s = 0
            for n in q:
                s += n.val
                if n.left:
                    tmp.append(n.left)
                if n.right:
                    tmp.append(n.right)
            res.append(s / len(q))
            q = tmp
        return res
```
