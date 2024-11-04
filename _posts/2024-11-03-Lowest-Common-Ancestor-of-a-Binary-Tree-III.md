---
layout:     post
title:      LeetCode 1650 Lowest Common Ancestor of a Binary Tree III (Python)
number:     1650
level:      Medium
lcurl:      lowest-common-ancestor-of-a-binary-tree-iii
youtube:    
bilibili1:  
xigua:      
date:       2024-11-03
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - HashTable
    - Two Pointers
---

### 题目

Given two nodes of a binary tree p and q, return their lowest common ancestor (LCA).

Each node will have a reference to its parent node. The definition for Node is below:

class Node {
    public int val;
    public Node left;
    public Node right;
    public Node parent;
}
According to the definition of LCA on Wikipedia: "The lowest common ancestor of two nodes p and q in a tree T is the lowest node that has both p and q as descendants (where we allow a node to be a descendant of itself)."

### 解题思路

方法一，从一个点开始遍历到根节点，记录路径上所有的点，再从另一个点向根节点遍历，遇到之前路径上的点位结果

方法二，类似求两个链表的交点，两个点同时向根遍历，如果p走到根，下一次走到q，如果q走到跟，下一个走到p，当两个点相交的时候，为结果

### 代码
```python
"""
# Definition for a Node.
class Node:
    def __init__(self, val):
        self.val = val
        self.left = None
        self.right = None
        self.parent = None
"""

class Solution:
    def lowestCommonAncestor(self, p: 'Node', q: 'Node') -> 'Node':
        visit = set()
        while p:
            visit.add(p)
            p = p.parent
        while q:
            if q in visit:
                return q
            q = q.parent
```
```python
class Solution:
    def lowestCommonAncestor(self, p: 'Node', q: 'Node') -> 'Node':
        p1, q1 = p, q
        while p1 != q1:
            p1 = p1.parent if p1.parent else q
            q1 = q1.parent if q1.parent else p
        return p1
```
