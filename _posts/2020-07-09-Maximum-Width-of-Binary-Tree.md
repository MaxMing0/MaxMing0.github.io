---
layout:     post
title:      LeetCode 662 Maximum Width of Binary Tree (Python)
number:     662
level:      Medium
lcurl:      maximum-width-of-binary-tree
youtube:    f9Ujzm94EPU
bilibili1:  //player.bilibili.com/player.html?aid=668760745&bvid=BV16a4y1h7fG&cid=210525928&page=1
xigua:      
date:       2020-06-09
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Tree
---

### 题目

Given a binary tree, write a function to get the maximum width of the given tree. The width of a tree is the maximum width among all levels. The binary tree has the same structure as a full binary tree, but some nodes are null.

The width of one level is defined as the length between the end-nodes (the leftmost and right most non-null nodes in the level, where the null nodes between the end-nodes are also counted into the length calculation.

### 解题思路

使用数组表示堆的方法来表示树中每个节点的位置，bfs遍历出每一层的节点，用最左和最右的两个节点求出宽度

### 代码
```python
class Solution:
    def widthOfBinaryTree(self, root: TreeNode) -> int:
        q = [(root, 0)]
        res = 1
        while q:
            res = max(res, q[-1][1] - q[0][1] + 1)
            tmp = []
            for node, pos in q:
                if node.left:
                    tmp.append((node.left, pos * 2))
                if node.right:
                    tmp.append((node.right, pos * 2 + 1))
            q = tmp
        return res
```
