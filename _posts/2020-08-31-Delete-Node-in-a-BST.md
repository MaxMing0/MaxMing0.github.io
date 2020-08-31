---
layout:     post
title:      LeetCode 450 Delete Node in a BST (Python)
number:     450
level:      Medium
lcurl:      delete-node-in-a-bst
youtube:    
bilibili1:  
xigua:      
date:       2020-08-31
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - BST
---

### 题目

Given a root node reference of a BST and a key, delete the node with the given key in the BST. Return the root node reference (possibly updated) of the BST.

Basically, the deletion can be divided into two stages:

- Search for a node to remove.
- If the node is found, delete the node.
Note: Time complexity should be O(height of tree).

### 解题思路

递归，从根开始遍历，如果要找的小于根，向左，大于，向右。如果为当前要删除的点，如果只有一边有子树，则将子树提上来，否则找到右子树中最小的数（最左边的叶子），把跟的数值变为这个值，并删除这个节点

### 代码
```python
class Solution:
    def deleteNode(self, root: TreeNode, key: int) -> TreeNode:
        if root is None:
            return root
        if root.val > key:
            root.left = self.deleteNode(root.left, key)
        elif root.val < key:
            root.right = self.deleteNode(root.right, key)
        else:
            if not root.left:
                return root.right
            if not root.right:
                return root.left
            tmp = root.right
            while tmp.left:
                tmp = tmp.left
            root.val = tmp.val
            root.right = self.deleteNode(root.right, tmp.val)
        return root
```
