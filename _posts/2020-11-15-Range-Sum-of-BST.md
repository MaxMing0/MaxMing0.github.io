---
layout:     post
title:      LeetCode 938 Range Sum of BST (Python)
number:     938
level:      Easy
lcurl:      range-sum-of-bst
youtube:    KvD7F0CAb8s
bilibili1:  //player.bilibili.com/player.html?aid=415306704&bvid=BV1WV411a7VR&cid=256111670&page=1
xigua:      
date:       2020-11-15
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - BST
---

### 题目

Given the root node of a binary search tree, return the sum of values of all nodes with a value in the range [low, high].

### 解题思路

递归，如果当前节点在范围内，加到结果里。如果当前节点大于low，遍历左子树，小于high，遍历右子树

### 代码
```python
class Solution:
    class Solution:
    def rangeSumBST(self, root: TreeNode, low: int, high: int) -> int:
        def dfs(root):
            if root:
                if low <= root.val <= high:
                    self.res += root.val
                if low < root.val:
                    dfs(root.left)
                if high > root.val:
                    dfs(root.right)
        self.res = 0
        dfs(root)
        return self.res
```
