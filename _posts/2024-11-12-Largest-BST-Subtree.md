---
layout:     post
title:      LeetCode 333 Largest BST Subtree (Python)
number:     333
level:      Medium
lcurl:      largest-bst-subtree
youtube:    
bilibili1:  
xigua:      
date:       2024-11-12
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - DFS
---

### 题目

Given the root of a binary tree, find the largest 
subtree
, which is also a Binary Search Tree (BST), where the largest means subtree has the largest number of nodes.

A Binary Search Tree (BST) is a tree in which all the nodes follow the below-mentioned properties:

- The left subtree values are less than the value of their parent (root) node's value.
- The right subtree values are greater than the value of their parent (root) node's value.
Note: A subtree must include all of its descendants.

### 解题思路

DFS,对于每个点，返回一个包含最小值，最大值和size的结构，只有当左子树的最大值<当前节点值<右子树最小值，该树才是bst，返回总节点数，否则返回最大的子树的节点数

### 代码
```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Node:
    def __init__(self, min_node, max_node, size):
        self.max_node = max_node
        self.min_node = min_node
        self.size = size
class Solution:
    def largestBSTSubtree(self, root: Optional[TreeNode]) -> int:
        def dfs(root):
            if not root:
                return Node(float('inf'), float('-inf'), 0)
            l = dfs(root.left)
            r = dfs(root.right)
            if l.max_node < root.val < r.min_node:
                return Node(min(root.val, l.min_node), max(root.val, r.max_node), l.size + r.size + 1)
            return Node(float('-inf'), float('inf'), max(l.size, r.size))

        return dfs(root).size
```
