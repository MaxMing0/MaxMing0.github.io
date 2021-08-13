---
layout:     post
title:      LeetCode 73 Set Matrix Zeroes (Python)
number:     73
level:      Medium
lcurl:      set-matrix-zeroes
youtube:    DZrav8lGXvU
bilibili1:  //player.bilibili.com/player.html?aid=762339721&bvid=BV1X64y1Y7kG&cid=388292645&page=1
xigua:      
date:       2021-08-13
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - 
---

### 题目

Given an m x n integer matrix matrix, if an element is 0, set its entire row and column to 0's, and return the matrix.

You must do it in place.

### 解题思路

方法1，使用一个数组存所有为0的位置，再遍历一次这个数组，更新所有位置

方法2，使用两个flag记录第一行和第一列是否有0，之后用第一行和第一列记录其他位置是否有0，最后更新整个矩阵

### 代码
```python
class Solution:
    def setZeroes(self, matrix: List[List[int]]) -> None:
        """
        Do not return anything, modify matrix in-place instead.
        """
        m, n = len(matrix), len(matrix[0])
        tmp = []
        for i in range(m):
            for j in range(n):
                if matrix[i][j] == 0:
                    tmp.append([i, j])
                    
        for r, c in tmp:
            for i in range(n):
                matrix[r][i] = 0
            for j in range(m):
                matrix[j][c] = 0
```
```python
class Solution:
    def setZeroes(self, matrix: List[List[int]]) -> None:
        """
        Do not return anything, modify matrix in-place instead.
        """
        m = len(matrix)
        n = len(matrix[0])
        fm = fn = 1
        for i in range(m):
            if matrix[i][0] == 0:
                fm = 0
                break
        for i in range(n):
            if matrix[0][i] == 0:
                fn = 0
                break
        for i in range(1, m):
            for j in range(1, n):
                if matrix[i][j] == 0:
                    matrix[i][0] = matrix[0][j] = 0
                    
        for i in range(1, m):
            if matrix[i][0] == 0:
                for j in range(1, n):
                    matrix[i][j] = 0
        for j in range(1, n):
            if matrix[0][j] == 0:
                for i in range(1, m):
                    matrix[i][j] = 0
                    
        if fm == 0:
            for i in range(m):
                matrix[i][0] = 0
        if fn == 0:
            for i in range(n):
                matrix[0][i] = 0
```
