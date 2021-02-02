---
layout:     post
title:      LeetCode 669 Trim a Binary Search Tree (Python)
number:     669
level:      Medium
lcurl:      trim-a-binary-search-tree
youtube:    NiooZ5GzzMM
bilibili1:  //player.bilibili.com/player.html?aid=801403536&bvid=BV19y4y1J7fu&cid=291818257&page=1
xigua:      
date:       2021-02-02
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - BST
---

### 题目

Given the root of a binary search tree and the lowest and highest boundaries as low and high, trim the tree so that all its elements lies in [low, high]. Trimming the tree should not change the relative structure of the elements that will remain in the tree (i.e., any node's descendant should remain a descendant). It can be proven that there is a unique answer.

Return the root of the trimmed binary search tree. Note that the root may change depending on the given bounds.

### 解题思路

递归，如果根小于low，递归trim右子树（根和左子树已经去掉），大于high，相反

### 代码
```python
class Solution:
    def trimBST(self, root: TreeNode, low: int, high: int) -> TreeNode:
        if not root:
            return None
        if root.val < low:
            return self.trimBST(root.right, low, high)
        if root.val > high:
            return self.trimBST(root.left, low, high)
        root.left = self.trimBST(root.left, low, high)
        root.right = self.trimBST(root.right, low, high)
        return root
```
