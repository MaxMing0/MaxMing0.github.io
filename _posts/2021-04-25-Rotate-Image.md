---
layout:     post
title:      LeetCode 48 Rotate Image (Python)
number:     48
level:      Medium
lcurl:      rotate-image
youtube:    kCy2FNX3jLU
bilibili1:  //player.bilibili.com/player.html?aid=802810069&bvid=BV1Wy4y1s7fs&cid=329300335&page=1
xigua:      
date:       2021-04-25
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - 
---

### 题目

You are given an n x n 2D matrix representing an image, rotate the image by 90 degrees (clockwise).

You have to rotate the image in-place, which means you have to modify the input 2D matrix directly. DO NOT allocate another 2D matrix and do the rotation.

### 解题思路

先reverse矩阵，之后沿着主对角线两两互换

### 代码
```python
class Solution:
    def rotate(self, matrix: List[List[int]]) -> None:
        """
        Do not return anything, modify matrix in-place instead.
        """
        matrix.reverse()
        for i in range(len(matrix)):
            for j in range(i):
                matrix[i][j], matrix[j][i] = matrix[j][i], matrix[i][j]
```
