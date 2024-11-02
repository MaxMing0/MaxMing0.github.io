---
layout:     post
title:      LeetCode 498 Diagonal Traverse (Python)
number:     498
level:      Medium
lcurl:      diagonal-traverse
youtube:    
bilibili1:  
xigua:      
date:       2024-11-01
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Array
---

### 题目

Given an m x n matrix mat, return an array of all the elements of the array in a diagonal order.

### 解题思路

i+j相同的数在一组，偶数翻转

### 代码
```python
class Solution:
    def findDiagonalOrder(self, matrix: List[List[int]]) -> List[int]:
        m = len(matrix)
        n = len(matrix[0])
        dic = defaultdict(list)
        for i in range(m):
            for j in range(n):
                dic[(i + j)].append(matrix[i][j])
        res = []
        for i in range(m + n - 1):
            if i % 2:
                res.extend(dic[i])
            else:
                res.extend(dic[i][::-1])
        return res
```
