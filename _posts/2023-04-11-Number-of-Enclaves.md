---
layout:     post
title:      LeetCode 1020 Number of Enclaves (Python)
number:     1020
level:      Medium
lcurl:      number-of-enclaves
youtube:    3rK-Vz849aY
bilibili1:  
xigua:      
date:       2023-04-11
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - BFS
    - DFS
---

### 题目

You are given an m x n binary matrix grid, where 0 represents a sea cell and 1 represents a land cell.

A move consists of walking from one land cell to another adjacent (4-directionally) land cell or walking off the boundary of the grid.

Return the number of land cells in grid for which we cannot walk off the boundary of the grid in any number of moves.

### 解题思路

从四周的陆地开始遍历，把遍历到的点标记为-1，剩下所有是1的点就是题目要找的

### 代码
```python
class Solution:
    def numEnclaves(self, grid: List[List[int]]) -> int:
        diretions = [[0, 1], [0, -1], [1, 0], [-1, 0]]
        def dfs(i, j):
            s = [(i, j)]
            while s:
                curx, cury = s.pop()
                if grid[curx][cury] == 1:
                    grid[curx][cury] = -1
                    for dx, dy in diretions:
                        tx = curx + dx
                        ty = cury + dy
                        if 0 <= tx < m and 0 <= ty < n and grid[tx][ty] == 1:
                            s.append((tx, ty))

        m, n = len(grid), len(grid[0])
        for i in range(n):
            dfs(0, i)
            dfs(m - 1, i)
        for i in range(m):
            dfs(i, 0)
            dfs(i, n - 1)
        res = 0
        for i in range(m):
            for j in range(n):
                if grid[i][j] == 1:
                    res += 1
        return res
```
