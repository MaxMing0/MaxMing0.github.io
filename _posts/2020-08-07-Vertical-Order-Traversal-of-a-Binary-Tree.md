---
layout:     post
title:      LeetCode 987 Vertical Order Traversal of a Binary Tree (Python)
number:     987
level:      Hard
lcurl:      vertical-order-traversal-of-a-binary-tree
youtube:    5DE2otSuDsw
bilibili1:  //player.bilibili.com/player.html?aid=371688036&bvid=BV1yZ4y1M7CL&cid=221550835&page=1
xigua:      
date:       2020-08-07
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Tree
---

### 题目

Given a binary tree, return the vertical order traversal of its nodes values.

For each node at position (X, Y), its left and right children respectively will be at positions (X-1, Y-1) and (X+1, Y-1).

Running a vertical line from X = -infinity to X = +infinity, whenever the vertical line touches some nodes, we report the values of the nodes in order from top to bottom (decreasing Y coordinates).

If two nodes have the same position, then the value of the node that is reported first is the value that is smaller.

Return an list of non-empty reports in order of X coordinate.  Every report will have a list of values of nodes.

### 解题思路

从根开始进行遍历，把每个节点的位置和层数存到字典中，最后一期求出结果

### 代码
```python
class Solution:
    def verticalTraversal(self, root: TreeNode) -> List[List[int]]:
        def dfs(root, pos, lvl):
            level[pos].append((lvl, root.val))
            if root.left:
                dfs(root.left, pos - 1, lvl + 1)
            if root.right:
                dfs(root.right, pos + 1, lvl + 1)
                
        level = defaultdict(list)
        q = [(root, 0, 0)]
        while q:
            cur, pos, lvl = q.pop()
            level[pos].append((lvl, cur.val))
            if cur.left:
                q.append((cur.left, pos - 1, lvl + 1))
            if cur.right:
                q.append((cur.right, pos + 1, lvl + 1))
        res = []
        for key, val in sorted(level.items(), key=lambda x: x[0]):
            res.append([v for k, v in sorted(val)])
        return res
```
