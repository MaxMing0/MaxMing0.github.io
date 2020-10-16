---
layout:     post
title:      LeetCode 74 Search a 2D Matrix (Python)
number:     74
level:      Medica
lcurl:      search-a-2d-matrix
youtube:    SgqNB-_o6YI
bilibili1:  //player.bilibili.com/player.html?aid=884911761&bvid=BV1aK4y1h7Bb&cid=246242225&page=1
xigua:      
date:       2020-10-16
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Binary Search
---

### 题目

Write an efficient algorithm that searches for a value in an m x n matrix. This matrix has the following properties:
- Integers in each row are sorted from left to right.
- The first integer of each row is greater than the last integer of the previous row.

### 解题思路

先对第一列进行二分，找到目标数可能出现的行，再对这一行进行二分

### 代码
```python
class Solution:
    def searchMatrix(self, matrix: List[List[int]], target: int) -> bool:
        m = len(matrix)
        if m == 0:
            return False
        n = len(matrix[0])
        if n == 0:
            return False
        if matrix[0][0] > target or matrix[m - 1][n - 1] < target:
            return False
        tmp = []
        for i in range(m):
            tmp.append(matrix[i][0])
        ind = bisect.bisect_left(tmp, target)
        if ind == len(tmp):
            ind = ind - 1
        if target < matrix[ind][0]:
            ind = ind - 1
        ind2 = bisect.bisect_left(matrix[ind], target)
        if ind2 == n:
            return False
        return matrix[ind][ind2] == target
```
