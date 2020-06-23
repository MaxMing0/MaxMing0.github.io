---
layout:     post
title:      LeetCode 222 Count Complete Tree Nodes (Python)
number:     222
level:      Medium
lcurl:      count-complete-tree-nodes
youtube:    tXe1NS4fgO4
bilibili1:  //player.bilibili.com/player.html?aid=201054349&bvid=BV1Qz411i7bh&cid=204958312&page=1
xigua:      
date:       2020-06-23
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Tree
---

### 题目

Given a complete binary tree, count the number of nodes.

### 解题思路

对于一个完全二叉树，树的高度为根节点到最左边叶节点的个数

如果这个树的左右子树高度相同，意味着左子树是满二叉树，否则右子树是满二叉树

### 代码
```python
class Solution:
    def countNodes(self, root: TreeNode) -> int:
        def get_height(root):
            return 1 + get_height(root.left) if root else -1

        res = 0
        h = get_height(root)
        if h < 0: 
            return 0
        while root:
            if get_height(root.right) == h - 1:
                res += 1 << h
                root = root.right
            else:
                res += 1 << (h - 1)
                root = root.left
            h -= 1
        return res
```
