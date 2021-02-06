---
layout:     post
title:      LeetCode 199 Binary Tree Right Side View (Python)
number:     199
level:      Medium
lcurl:      binary-tree-right-side-view
youtube:    uu5cwzOUU38
bilibili1:  //player.bilibili.com/player.html?aid=844043854&bvid=BV1854y1W7CB&cid=293762506&page=1
xigua:      
date:       2021-02-06
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - DFS
---

### 题目

Given a binary tree, imagine yourself standing on the right side of it, return the values of the nodes you can see ordered from top to bottom.

### 解题思路

使用字典存每一行的最右边元素，使用dfs遍历左右子树同时维护结点的深度，每次出现新的深度，该节点为最右边节点

### 代码
```python
class Solution:
    def rightSideView(self, root: TreeNode) -> List[int]:
        if not root:
            return []
        res, max_depth = {}, 0
        stack = [(root, 0)]
        while stack:
            cur, depth = stack.pop()
            max_depth = max(max_depth, depth)
            res.setdefault(depth, cur.val)
            if cur.left:
                stack.append((cur.left, depth + 1))
            if cur.right:
                stack.append((cur.right, depth + 1))
        return [res[depth] for depth in range(max_depth + 1)]
```
