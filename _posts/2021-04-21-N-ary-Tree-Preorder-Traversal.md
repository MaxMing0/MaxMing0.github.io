---
layout:     post
title:      LeetCode 589 N-ary Tree Preorder Traversal (Python)
number:     589
level:      Easy
lcurl:      n-ary-tree-preorder-traversal
youtube:    CFJ4Kgw1FFo
bilibili1:  //player.bilibili.com/player.html?aid=375182344&bvid=BV1io4y1f7qT&cid=327546342&page=1
xigua:      
date:       2021-04-21
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Tree
---

### 题目

Given the root of an n-ary tree, return the preorder traversal of its nodes' values.

Nary-Tree input serialization is represented in their level order traversal. Each group of children is separated by the null value (See examples)

### 解题思路

递归，先将根加入结果里，然后遍历所有子树

### 代码
```python
class Solution:
    def preorder(self, root: 'Node') -> List[int]:
        def dfs(root):
            if root:
                res.append(root.val)
                for child in root.children:
                    dfs(child)    
        res = []
        dfs(root)
        return res
```
