---
layout:     post
title:      LeetCode 1305 All Elements in Two Binary Search Trees (Python)
number:     1305
level:      Medium
lcurl:      all-elements-in-two-binary-search-trees
youtube:    zqroKmPUgAY
bilibili1:  
xigua:      
date:       2020-09-05
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - BST
---

### 题目

Given two binary search trees root1 and root2.

Return a list containing all the integers from both trees sorted in ascending order.

### 解题思路

对两棵树进行中序遍历，遍历的结果为从小到大排序，再进行一次归并排序

### 代码
```python
class Solution:
    def getAllElements(self, root1: TreeNode, root2: TreeNode) -> List[int]:
        def dfs(node, n):
            if not node:
                return
            dfs(node.left, n)
            n.append(node.val)
            dfs(node.right, n)
        
        n1, n2 = [], []
        dfs(root1, n1)
        dfs(root2, n2)
        res, i, j = [], 0, 0
        while i < len(n1) and j < len(n2):
            if n1[i] <= n2[j]:
                res.append(n1[i])
                i += 1
            else:
                res.append(n2[j])
                j += 1
        res.extend(n1[i:])
        res.extend(n2[j:])
        return res
```
```python
class Solution:
    def getAllElements(self, root1: TreeNode, root2: TreeNode) -> List[int]:
        res, s1, s2 = [], [], []
        while root1 or s1 or root2 or s2:
            while root1:
                s1.append(root1)
                root1 = root1.left
            while root2:
                s2.append(root2)
                root2 = root2.left

            if s1 and s2:
                if s1[-1].val <= s2[-1].val:
                    node = s1.pop()
                    res.append(node.val)
                    root1 = node.right
                else:
                    node = s2.pop()
                    res.append(node.val)
                    root2 = node.right
            elif not s1:
                node = s2.pop()
                res.append(node.val)
                root2 = node.right
            else:
                node = s1.pop()
                res.append(node.val)
                root1 = node.right
        return res
```
