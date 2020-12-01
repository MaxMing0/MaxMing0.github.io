---
layout:     post
title:      LeetCode 104 Maximum Depth of Binary Tree (Python)
number:     104
level:      Easy
lcurl:      maximum-depth-of-binary-tree
youtube:    bvlZtjipGU0
bilibili1:  //player.bilibili.com/player.html?aid=500498559&bvid=BV1tK41137GM&cid=261713667&page=1
xigua:      
date:       2020-12-01
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Tree
---

### 题目

Given the root of a binary tree, return its maximum depth.

A binary tree's maximum depth is the number of nodes along the longest path from the root node down to the farthest leaf node.

### 解题思路

递归：深度为左右子树最大深度+1

非递归：从根开始bfs，每做一层，结果+1

### 代码
```python
class Solution:
    def maxDepth(self, root: TreeNode) -> int:
        return max(self.maxDepth(root.left), self.maxDepth(root.right)) + 1 if root else 0
```

```python
class Solution:
    def maxDepth(self, root: TreeNode) -> int:
        if not root:
            return 0
        q = [root]
        res = 0
        while q:
            tq = []
            for n in q:
                if n.left:
                    tq.append(n.left)
                if n.right:
                    tq.append(n.right)
            q = tq
            res += 1
        return res
```
