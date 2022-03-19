---
layout:     post
title:      LeetCode 95 Unique Binary Search Trees II (Python)
number:     95
level:      Easy
lcurl:      unique-binary-search-trees-ii
youtube:    Gk4iwl0zTkA
bilibili1:  
xigua:      
date:       2022-03-18
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Recursive
---

### 题目

Given an integer n, return all the structurally unique BST's (binary search trees), which has exactly n nodes of unique values from 1 to n. Return the answer in any order.

### 解题思路

枚举每个数当根，对左右两边的数递归简历子树

### 代码
```python
class Solution:        
    def generateTrees(self, n: int) -> List[TreeNode]:
        def gen(l, r):
            ret = []
            if l > r:
                return [None]
            
            for i in range(l, r + 1):
                left = gen(l, i - 1)
                right = gen(i + 1, r)
                for lnode in left:
                    for rnode in right:
                        root = TreeNode(i)
                        root.left = lnode
                        root.right = rnode
                        ret.append(root)
            return ret
    
        return gen(1, n)
```
