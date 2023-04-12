---
layout:     post
title:      Leetcode 1254 Number of Closed Islands (Python)
number:     1254
level:      Medium
lcurl:      number-of-closed-islands
youtube:    T9nJtcktnas
bilibili1:  
xigua:      
date:       2022-04-11
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - BFS
    - DFS
---

### 题目

Given a 2D grid consists of 0s (land) and 1s (water).  An island is a maximal 4-directionally connected group of 0s and a closed island is an island totally (all left, top, right, bottom) surrounded by 1s.

Return the number of closed islands.

### 解题思路

扫描整个矩阵，如果找到没遍历过的陆地，就从这里进行搜索，如果遍历到边界就不是岛，否则就是一个岛

### 代码
```python
class Solution:
    def closedIsland(self, grid: List[List[int]]) -> int:
        def dfs(i, j):
            s = [(i, j)]
            visited.add((i, j))
            directions = [(0, 1), (0, -1), (1, 0), (-1, 0)]
            ret = 1
            while s:
                curx, cury = s.pop()
                for dirx, diry in directions:
                    tx, ty = curx + dirx, cury + diry
                    if tx < 0 or tx >= m or ty < 0 or ty >= n:
                        ret = 0
                        continue
                    if grid[tx][ty] == 0 and (tx, ty) not in visited:
                        s.append((tx, ty))
                        visited.add((tx, ty))
            return ret

        m, n = len(grid), len(grid[0])
        visited = set()
        res = 0
        for i in range(m):
            for j in range(n):
                if grid[i][j] == 0 and (i, j) not in visited:
                    res += dfs(i, j)
        return res
```
