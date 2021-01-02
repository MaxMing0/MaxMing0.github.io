---
layout:     post
title:      LeetCode 1379 Find a Corresponding Node of a Binary Tree in a Clone of That Tree (Python)
number:     1379
level:      Medium
lcurl:      find-a-corresponding-node-of-a-binary-tree-in-a-clone-of-that-tree
youtube:    NKKcmMdxUN4
bilibili1:  //player.bilibili.com/player.html?aid=843489880&bvid=BV1A54y147HN&cid=276291119&page=1
xigua:      
date:       2020-01-02
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Tree
---

### 题目

Given two binary trees original and cloned and given a reference to a node target in the original tree.

The cloned tree is a copy of the original tree.

Return a reference to the same node in the cloned tree.

Note that you are not allowed to change any of the two trees or the target node and the answer must be a reference to a node in the cloned tree.

Follow up: Solve the problem if repeated values on the tree are allowed.

### 解题思路

使用前序遍历同时递归两棵树，当在origin找到目标节点时，返回cloned树中对应节点

### 代码
```python
class Solution:
    def getTargetCopy(self, original: TreeNode, cloned: TreeNode, target: TreeNode) -> TreeNode:
        if original == target:
            return cloned
        if original.left:
            res = self.getTargetCopy(original.left, cloned.left, target)
            if res:
                return res
        if original.right:
            res = self.getTargetCopy(original.right, cloned.right, target)
            if res:
                return res
```
