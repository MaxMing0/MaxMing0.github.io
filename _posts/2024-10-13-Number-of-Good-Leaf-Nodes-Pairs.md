---
layout:     post
title:      LeetCode 1530 Number of Good Leaf Nodes Pairs (Python)
number:     1530
level:      Medium
lcurl:      number-of-good-leaf-nodes-pairs
youtube:    
bilibili1:  
xigua:      
date:       2024-10-13
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - 
---

### 题目

You are given the root of a binary tree and an integer distance. A pair of two different leaf nodes of a binary tree is said to be good if the length of the shortest path between them is less than or equal to distance.

Return the number of good leaf node pairs in the tree.

### 解题思路

dfs,返回到当前节点，有多少个距离为多少的节点，然后组合左右子树的结果，返回上一层

### 代码
```python
class Solution:
    def countPairs(self, root: TreeNode, distance: int) -> int:
        self.res = 0
        def dfs(root):
            d1 = distance + 1
            tmp_left, tmp_right, tmp = [0] * d1, [0] * d1, [0] * d1
            if not root.left and not root.right:
                tmp[0] = 1
                return tmp
            left, right = [], []
            if root.left:
                left = dfs(root.left)
            if root.right:
                right = dfs(root.right)
            if left:
                for i in range(distance):
                    tmp_left[i + 1] = left[i]
            if right:
                for i in range(distance):
                    tmp_right[i + 1] = right[i]
            if not left:
                return tmp_right
            if not right:
                return tmp_left
            tot = 0
            for i in range(d1):
                for j in range(d1):
                    if i + j > distance:
                        continue
                    tot += tmp_left[i] * tmp_right[j]
            self.res += tot
            for i in range(distance + 1):
                tmp[i] = tmp_left[i] + tmp_right[i]
            return tmp

        dfs(root)
        return self.res
```
