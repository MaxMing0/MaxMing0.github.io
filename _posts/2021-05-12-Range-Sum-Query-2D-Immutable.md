---
layout:     post
title:      LeetCode 304 Range Sum Query 2D - Immutable (Python)
number:     304
level:      Medium
lcurl:      range-sum-query-2d-immutable
youtube:    nC1q20ndxy0
bilibili1:  //player.bilibili.com/player.html?aid=758036768&bvid=BV1R64y127jL&cid=337897862&page=1
xigua:      
date:       2021-05-12
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - 
---

### 题目

Given a 2D matrix matrix, handle multiple queries of the following type:

1. Calculate the sum of the elements of matrix inside the rectangle defined by its upper left corner (row1, col1) and lower right corner (row2, col2).
Implement the NumMatrix class:

- NumMatrix(int[][] matrix) Initializes the object with the integer matrix matrix.
- int sumRegion(int row1, int col1, int row2, int col2) Returns the sum of the elements of matrix inside the rectangle defined by its upper left corner (row1, col1) and lower right corner (row2, col2).

### 解题思路

二维的部分和，summ[i, j]表示从(0,0)到(i-1, j-1)矩阵的和

结果为 summ[row2 + 1][col2 + 1] - summ[row2 + 1][col1] - summ[row1][col2 + 1] + summ[row1][col1]

### 代码
```python
class NumMatrix(object):

    def __init__(self, matrix):
        """
        :type matrix: List[List[int]]
        """
        m = len(matrix)
        n = len(matrix[0]) if m > 0 else 0
        self.summ = [[0] * (n + 1) for _ in range(m + 1)]
        for i in range(1, m + 1):
            for j in range(1, n + 1):
                self.summ[i][j] = self.summ[i - 1][j] + self.summ[i][j - 1] - self.summ[i - 1][j - 1] + matrix[i - 1][j - 1]

    def sumRegion(self, row1, col1, row2, col2):
        """
        :type row1: int
        :type col1: int
        :type row2: int
        :type col2: int
        :rtype: int
        """
        return self.summ[row2 + 1][col2 + 1] - self.summ[row2 + 1][col1] - self.summ[row1][col2 + 1] + self.summ[row1][col1]
```
