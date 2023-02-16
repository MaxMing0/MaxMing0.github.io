---
layout:     post
title:      LeetCode 1162 As Far from Land as Possible (Python)
number:     1162
level:      Medium
lcurl:      as-far-from-land-as-possible
youtube:    b2vDIPRKib0
bilibili1:  
xigua:      
date:       2023-02-15
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - BFS
---

### 题目

Given an `n x n` grid containing only values `0` and `1`, where `0` represents water and `1` represents land, find a water cell such that its distance to the nearest land cell is maximized, and return the distance. If no land or water exists in the grid, return `-1`.

The distance used in this problem is the Manhattan distance: the distance between two cells `(x0, y0)` and `(x1, y1)` is `|x0 - x1| + |y0 - y1|`.

### 解题思路

从所有陆地开始进行BFS，每次遍历相邻的单元格，最后遍历到的单元格为距离最远的位置，变成的次数就是结果

### 代码
```python
class Solution:
    class Solution:
    def maxDistance(self, grid: List[List[int]]) -> int:
        directions = [(0, 1), (0, -1), (1, 0), (-1, 0)]
        n = len(grid)
        q = []
        for i in range(n):
            for j in range(n):
                if grid[i][j] == 1:
                    q.append((i, j))
        res = 0
        rem = n * n - len(q)
        while len(q) > 0 and rem > 0:
            tmp = []
            for x, y in q:
                for dx, dy in directions:
                    tx, ty = x + dx, y + dy
                    if 0 <= tx < n and 0 <= ty < n and grid[tx][ty] == 0:
                        tmp.append((tx, ty))
                        grid[tx][ty] = 1
            q = tmp
            rem -= len(q)
            res += 1
        return res if res > 0 else -1
```
