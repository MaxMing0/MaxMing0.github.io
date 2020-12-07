---
layout:     post
title:      LeetCode 59 Spiral Matrix II (Python)
number:     59
level:      Medium
lcurl:      spiral-matrix-ii
youtube:    MxHBooHLlt0
bilibili1:  //player.bilibili.com/player.html?aid=458123291&bvid=BV1q5411G7MY&cid=263969732&page=1
xigua:      
date:       2020-12-07
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - 
---

### 题目

Given a positive integer n, generate an n x n matrix filled with elements from 1 to n2 in spiral order.

### 解题思路

根据方向和下一个填充的位置的对应，找到下一个位置，如果这个位置出边界或已经被填过，则转换方向

### 代码
```python
class Solution:
    def generateMatrix(self, n: int) -> List[List[int]]:
        res = [[0] * n for _ in range(n)]
        directions = [(0, 1), (1, 0), (0, -1), (-1, 0)]
        curx = cury = curd = 0
        for i in range(1, n * n + 1):
            res[curx][cury] = i
            newx, newy = curx + directions[curd][0], cury + directions[curd][1]
            if newx < 0 or newx >= n or newy < 0 or newy >= n or res[newx][newy]:
                curd = (curd + 1) % 4
            curx += directions[curd][0]
            cury += directions[curd][1]
        return res
```
