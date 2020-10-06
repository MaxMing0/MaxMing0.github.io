---
layout:     post
title:      LeetCode 701 Insert into a Binary Search Tree (Python)
number:     701
level:      Medium
lcurl:      insert-into-a-binary-search-tree
youtube:    pPy6csnf4sk
bilibili1:  //player.bilibili.com/player.html?aid=842334333&bvid=BV1q54y1k76s&cid=242774417&page=1
xigua:      
date:       2020-10-06
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - BST
---

### 题目

You are given the root node of a binary search tree (BST) and a value to insert into the tree. Return the root node of the BST after the insertion. It is guaranteed that the new value does not exist in the original BST.

Notice that there may exist multiple valid ways for the insertion, as long as the tree remains a BST after insertion. You can return any of them.

### 解题思路

递归，如果比根小插入到左子树，否则插入到右子树，如果根是空，这将这个数插到这里

### 代码
```python
class Solution:
    def insertIntoBST(self, root: TreeNode, val: int) -> TreeNode:
        if not root:
            return TreeNode(val)
        if val > root.val:
            root.right = self.insertIntoBST(root.right, val)
        else:
            root.left = self.insertIntoBST(root.left, val)
        return root
```
