---
layout:     post
title:      LeetCode 1644 Lowest Common Ancestor of a Binary Tree II (Python)
number:     1644
level:      Medium
lcurl:      lowest-common-ancestor-of-a-binary-tree-ii
youtube:    
bilibili1:  
xigua:      
date:       2024-11-03
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - DFS
---

### 题目

Given the root of a binary tree, return the lowest common ancestor (LCA) of two given nodes, p and q. If either node p or q does not exist in the tree, return null. All values of the nodes in the tree are unique.

According to the definition of LCA on Wikipedia: "The lowest common ancestor of two nodes p and q in a binary tree T is the lowest node that has both p and q as descendants (where we allow a node to be a descendant of itself)". A descendant of a node x is a node y that is on the path from node x to some leaf node.

### 解题思路

从root开始使用dfs，返回是否遇到p或者q，如果左右子树均找到p或者q，这个节点为结果，否则返回找到的子树。在遍历的过程中，如果遇到p或者q则更新全局找到了p或者q，如果在遍历之后并没有都找到p和q，返回空，否则返回结果

### 代码
```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    found_p = False
    found_q = False
    def lowestCommonAncestor(self, root: 'TreeNode', p: 'TreeNode', q: 'TreeNode') -> 'TreeNode':
        def LCA(root, p, q):
            if not root:
                return root
            left = LCA(root.left, p, q)
            right = LCA(root.right, p, q)
            if root.val == p.val:
                self.found_p = True
                return root
            if root.val == q.val:
                self.found_q = True
                return root
            return root if left and right else left or right
        
        res = LCA(root, p, q)
        if self.found_p and self.found_q:
            return res
        return None
```
