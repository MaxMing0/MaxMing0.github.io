---
layout:     post
title:      LeetCode 113 Path Sum II (Python)
number:     113
level:      Medium
lcurl:      path-sum-ii
youtube:    -RntttGyGSM
bilibili1:  //player.bilibili.com/player.html?aid=847139396&bvid=BV1k54y177fu&cid=383388423&page=1
xigua:      
date:       2021-08-03
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - DFS
    - BFS
---

### 题目

Given the root of a binary tree and an integer targetSum, return all root-to-leaf paths where each path's sum equals targetSum.

A leaf is a node with no children.

### 解题思路

从根开始进行BFS或者DFS，遍历的时候维护路径和当前的和，到达叶节点判断是否等于target，如果是加到结果里

### 代码
```python
class Solution:
    def pathSum(self, root: TreeNode, targetSum: int) -> List[List[int]]:
        if not root:
            return []
        q = [(root, root.val, [root.val])]
        res = []
        while q:
            cur, s, path = q.pop()
            if not cur.left and not cur.right and s == targetSum:
                res.append(path)
            if cur.left:
                q.append((cur.left, s + cur.left.val, path + [cur.left.val]))
            if cur.right:
                q.append((cur.right, s + cur.right.val, path + [cur.right.val]))
        return res
```
