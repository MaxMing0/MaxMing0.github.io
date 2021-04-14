---
layout:     post
title:      LeetCode 1302 Deepest Leaves Sum (Python)
number:     1302
level:      deepest-leaves-sum
lcurl:      Medium
youtube:    7DgfA2brCic
bilibili1:  //player.bilibili.com/player.html?aid=630124109&bvid=BV1Bb4y1D7Cp&cid=324313356&page=1
xigua:      
date:       2021-04-14
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - 
---

### 题目

Given the root of a binary tree, return the sum of values of its deepest leaves.

### 解题思路

按层进行BFS，如果下一层没有新的节点，返回当前层所有数的和

### 代码
```python
class Solution:
    def deepestLeavesSum(self, root: TreeNode) -> int:
        q = [root]
        while q:
            tmp = []
            for node in q:
                if node.left:
                    tmp.append(node.left)
                if node.right:
                    tmp.append(node.right)
            if not tmp:
                return sum([n.val for n in q])
            q = tmp
```
