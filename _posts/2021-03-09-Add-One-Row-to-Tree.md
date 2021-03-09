---
layout:     post
title:      LeetCode 623 Add One Row to Tree (Python)
number:     623
level:      Medium
lcurl:      add-one-row-to-tree
youtube:    A3fLuylaLN0
bilibili1:  //player.bilibili.com/player.html?aid=929580063&bvid=BV1AK4y1U7ud&cid=308063464&page=1
xigua:      
date:       2021-03-09
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Tree
---

### 题目

Given the root of a binary tree, then value v and depth d, you need to add a row of nodes with value v at the given depth d. The root node is at depth 1.

The adding rule is: given a positive integer depth d, for each NOT null tree nodes N in depth d-1, create two tree nodes with value v as N's left subtree root and right subtree root. And N's original left subtree should be the left subtree of the new left subtree root, its original right subtree should be the right subtree of the new right subtree root. If depth d is 1 that means there is no depth d-1 at all, then create a tree node with value v as the new root of the whole original tree, and the original tree is the new root's left subtree.

### 解题思路

BFS到需要插入节点的那一层，对于每个节点，向左右子树分别插入要求节点，并让左子树的左子树和右子树的右子树指向之前的左右子树

### 代码
```python
class Solution:
    def addOneRow(self, root: TreeNode, v: int, d: int) -> TreeNode:
        if d == 1:
            n = TreeNode(v)
            n.left = root
            return n
        q = [root]
        for _ in range(d - 2):
            tmp = []
            for n in q:
                if n.left:
                    tmp.append(n.left)
                if n.right:
                    tmp.append(n.right)
            q = tmp
        for node in q:
            tmp = node.left;
            node.left = TreeNode(v);
            node.left.left = tmp;
            tmp = node.right;
            node.right = TreeNode(v);
            node.right.right = tmp;
        return root
```
