---
layout:     post
title:      LeetCode 103 Binary Tree Zigzag Level Order Traversal (Python)
number:     103
level:      Medium
lcurl:      binary-tree-zigzag-level-order-traversal
youtube:    ccJ8a2VuAes
bilibili1:  //player.bilibili.com/player.html?aid=201495721&bvid=BV15h411Z7h5&cid=215333719&page=1
xigua:      
date:       2020-07-22
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Tree
---

### 题目

Given a binary tree, return the zigzag level order traversal of its nodes' values. (ie, from left to right, then right to left for the next level and alternate between).

### 解题思路

对树进行前序遍历，同时记录层数，将每层的节点放到一个双向队列中，偶数层向右加，奇数层向左加

### 代码
```python
class Solution:
    def zigzagLevelOrder(self, root: TreeNode) -> List[List[int]]:
        def dfs(root, lev):
            if lev < len(res):
                if lev % 2:
                    res[lev].appendleft(root.val)
                else:
                    res[lev].append(root.val)
            else:
                res.append(deque([root.val]))
            if root.left:
                dfs(root.left, lev + 1)
            if root.right:
                dfs(root.right, lev + 1)
        
        if not root:
            return []
        res = []
        dfs(root, 0)
        return res
```
