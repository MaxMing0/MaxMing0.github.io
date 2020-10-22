---
layout:     post
title:      LeetCode 111 Minimum Depth of Binary Tree (Python)
number:     111
level:      Easy
lcurl:      minimum-depth-of-binary-tree
youtube:    5kNck5XXJnU
bilibili1:  //player.bilibili.com/player.html?aid=372527173&bvid=BV1XZ4y1G7xM&cid=248308341&page=1
xigua:      
date:       2020-10-22
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Tree
    - BFS
---

### 题目

Given a binary tree, find its minimum depth.

The minimum depth is the number of nodes along the shortest path from the root node down to the nearest leaf node.

Note: A leaf is a node with no children.

### 解题思路

从根节点开始进行BFS，记录深度，遇到的第一个叶节点就是答案

### 代码
```python
class Solution:
    def minDepth(self, root: TreeNode) -> int:
        if not root:
            return 0
        q = [(root, 1)]
        while q:
            cur, depth = q.pop(0)
            if not cur.left and not cur.right:
                return depth
            if cur.left:
                q.append((cur.left, depth + 1))
            if cur.right:
                q.append((cur.right, depth + 1))
```
