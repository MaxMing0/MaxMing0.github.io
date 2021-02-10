---
layout:     post
title:      LeetCode 538 Convert BST to Greater Tree (Python)
number:     538
level:      Medium
lcurl:      convert-bst-to-greater-tree
youtube:    1H0zkhu6y4A
bilibili1:  //player.bilibili.com/player.html?aid=459080036&bvid=BV1k541177bt&cid=295689763&page=1
xigua:      
date:       2021-02-09
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - BST
---

### 题目

Given the root of a Binary Search Tree (BST), convert it to a Greater Tree such that every key of the original BST is changed to the original key plus sum of all keys greater than the original key in BST.

As a reminder, a binary search tree is a tree that satisfies these constraints:

- The left subtree of a node contains only nodes with keys less than the node's key.
- The right subtree of a node contains only nodes with keys greater than the node's key.
- Both the left and right subtrees must also be binary search trees.
Note: This question is the same as 1038: https://leetcode.com/problems/binary-search-tree-to-greater-sum-tree/

### 解题思路

使用右根左的顺序遍历，遍历的时候记录所有经过节点的总和，更新当前节点

### 代码
```python
class Solution:
    def convertBST(self, root: TreeNode) -> TreeNode:
        def dfs(root):
            if not root:
                return
            dfs(root.right)
            self.ct += root.val
            root.val = self.ct
            dfs(root.left)
        self.ct = 0
        dfs(root)
        return root
```
