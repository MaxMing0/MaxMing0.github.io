---
layout:     post
title:      LeetCode 106 Construct Binary Tree from Inorder and Postorder Traversal (Python)
number:     106
level:      Medium
lcurl:      construct-binary-tree-from-inorder-and-postorder-traversal
youtube:    HPC2xuP4gm0
bilibili1:  //player.bilibili.com/player.html?aid=201505120&bvid=BV1jh411Z7y8&cid=217385035&page=1
xigua:      
date:       2020-07-27
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Tree
---

### 题目

Given inorder and postorder traversal of a tree, construct the binary tree.

### 解题思路

通过后序遍历找到根，通过根的位置再中序遍历中划分出左右子树，确定左右子树在两个遍历中的起始位置，进行递归

### 代码
```python
class Solution:
    def buildTree(self, inorder: List[int], postorder: List[int]) -> TreeNode:
        def build(ini, inj, posti, postj):
            if ini == inj:
                return TreeNode(inorder[ini])
            rootval = postorder[postj]
            ind = dic[rootval]
            res = TreeNode(rootval)

            leftin1 = ini
            rightin1 = ind - 1
            leftpost1 = posti
            rightpost1 = posti + rightin1 - leftin1

            leftin2 = ind + 1
            rightin2 = inj
            leftpost2 = rightpost1 + 1
            rightpost2 = postj - 1
            
            if rightin1 >= leftin1:
                res.left = build(leftin1, rightin1, leftpost1, rightpost1)
            if rightin2 >= leftin2:
                res.right = build(leftin2, rightin2, leftpost2, rightpost2)
            return res
        
        dic = {n: i for i, n in enumerate(inorder)}
        if not inorder:
            return None
        return build(0, len(inorder) - 1, 0, len(postorder) - 1)
```
