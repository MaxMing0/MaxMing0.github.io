---
layout:     post
title:      LeetCode 766 Toeplitz Matrix (Python)
number:     766
level:      Easy
lcurl:      toeplitz-matrix
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

Given an m x n matrix, return true if the matrix is Toeplitz. Otherwise, return false.

A matrix is Toeplitz if every diagonal from top-left to bottom-right has the same elements.

### 解题思路

只遍历`m-1` * `n-1`的数组，遍历到i，j时判断和i+1，j+1 是否相等

### 代码
```python
class Solution:
    def isToeplitzMatrix(self, matrix: List[List[int]]) -> bool:
        for i in range(len(matrix) - 1):
            for j in range(len(matrix[0]) - 1):
                if matrix[i][j] != matrix[i + 1][j + 1]:
                    return False
        return True
```
