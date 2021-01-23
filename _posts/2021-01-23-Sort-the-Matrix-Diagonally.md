---
layout:     post
title:      LeetCode 1329 Sort the Matrix Diagonally (Python)
number:     1329
level:      Medium
lcurl:      sort-the-matrix-diagonally
youtube:    6ybXtlW69wM
bilibili1:  //player.bilibili.com/player.html?aid=671280839&bvid=BV1hU4y147b1&cid=286386598&page=1
xigua:      
date:       2021-01-23
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Hash Table
---

### 题目

A matrix diagonal is a diagonal line of cells starting from some cell in either the topmost row or leftmost column and going in the bottom-right direction until reaching the matrix's end. For example, the matrix diagonal starting from mat[2][0], where mat is a 6 x 3 matrix, includes cells mat[2][0], mat[3][1], and mat[4][2].

Given an m x n matrix mat of integers, sort each matrix diagonal in ascending order and return the resulting matrix.

### 解题思路

同一对角线的坐标差相同，使用字典加优先队列把相同对角线的数排序，依次pop重建

### 代码
```python
class Solution:
    def diagonalSort(self, mat: List[List[int]]) -> List[List[int]]:
        dic = defaultdict(list)
        m, n = len(mat), len(mat[0])
        for i in range(m):
            for j in range(n):
                heappush(dic[i - j], mat[i][j])
        for i in range(m):
            for j in range(n):
                mat[i][j] = heappop(dic[i - j])
        return mat
```
