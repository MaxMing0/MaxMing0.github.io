---
layout:     post
title:      LeetCode 463 Island Perimeter (Python)
number:     463
level:      Easy
lcurl:      island-perimeter
youtube:    2ab0w8TTB2A
bilibili1:  //player.bilibili.com/player.html?aid=413813095&bvid=BV16V41167bF&cid=209824913&page=1
xigua:      
date:       2020-07-07
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - 
---

### 题目

You are given a map in form of a two-dimensional integer grid where 1 represents land and 0 represents water.

Grid cells are connected horizontally/vertically (not diagonally). The grid is completely surrounded by water, and there is exactly one island (i.e., one or more connected land cells).

The island doesn't have "lakes" (water inside that isn't connected to the water around the island). One cell is a square with side length 1. The grid is rectangular, width and height don't exceed 100. Determine the perimeter of the island.

### 解题思路

遇到陆地边长+4，如果上边或左边有相邻土地，分别减2

### 代码
```python
class Solution:
    def islandPerimeter(self, grid: List[List[int]]) -> int:
        m = len(grid)
        n = len(grid[0])
        res = 0
        for i in range(m):
            for j in range(n):
                if grid[i][j] == 1:
                    res += 4
                    if i > 0 and grid[i - 1][j] == 1:
                        res -= 2
                    if j > 0 and grid[i][j - 1] == 1:
                        res -= 2
        return res
```
