---
layout:     post
title:      LeetCode 863 All Nodes Distance K in Binary Tree (Python)
number:     863
level:      Medium
lcurl:      all-nodes-distance-k-in-binary-tree
youtube:    
bilibili1:  
xigua:      
date:       2024-11-01
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - BFS
---

### 题目

Given the root of a binary tree, the value of a target node target, and an integer k, return an array of the values of all nodes that have a distance k from the target node.

You can return the answer in any order.

### 解题思路

预处理一个字典parent，从根开始BFS，记录每个结点的父节点。再从target结点开始BFS，向左右子树和父节点进行遍历，找到所有距离为k的点

### 代码
```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    def distanceK(self, root: TreeNode, target: TreeNode, k: int):
        if k == 0:
            return [target.val]
        p = {}
        s = [root]
        while s:
            cur = s.pop()
            if cur.left:
                s.append(cur.left)
                p[cur.left.val] = cur
            if cur.right:
                s.append(cur.right)
                p[cur.right.val] = cur
        visited = {target.val}
        q = [target]
        while q:
            tmp = []
            for n in q:
                if n.left and (n.left.val not in visited):
                    tmp.append(n.left)
                    visited.add(n.left.val)
                if n.right and (n.right.val not in visited):
                    tmp.append(n.right)
                    visited.add(n.right.val)
                if (n.val in p) and (p[n.val].val not in visited):
                    tmp.append(p[n.val])
                    visited.add(p[n.val].val)
            k -= 1
            if k == 0:
                return [n.val for n in tmp]
            q = tmp[:]
        return []
```
