---
layout:     post
title:      LeetCode 200 Number of Islands (Python)
number:     200
level:      Medium
lcurl:      number-of-islands
youtube:    ImBqGrGgzp0
bilibili1:  //player.bilibili.com/player.html?aid=582764896&bvid=BV1E64y1T7Nk&cid=179580114&page=1
xigua:      
date:       2020-04-26
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - DFS
    - BFS
    - Union Find
---

### 题目

Given a 2d grid map of '1's (land) and '0's (water), count the number of islands. An island is surrounded by water and is formed by connecting adjacent lands horizontally or vertically. You may assume all four edges of the grid are all surrounded by water.

### 解题思路



### 代码
```python
class Solution:
    def numIslands(self, grid: List[List[str]]) -> int:
        def dfs(i, j):
            grid[i][j] = '0'
            q = [(i, j)]
            while q:
                x, y = q.pop()
                if x > 0 and grid[x - 1][y] == '1':
                    grid[x - 1][y] = '0'
                    q.append((x - 1, y))
                if y > 0 and grid[x][y - 1] == '1':
                    grid[x][y - 1] = '0'
                    q.append((x, y - 1))
                if x < m - 1 and grid[x + 1][y] == '1':
                    grid[x + 1][y] = '0'
                    q.append((x + 1, y))
                if y < n - 1 and grid[x][y + 1] == '1':
                    grid[x][y + 1] = '0'
                    q.append((x, y + 1))
                
        m = len(grid)
        if m == 0:
            return 0
        n = len(grid[0])
        res = 0
        for i in range(m):
            for j in range(n):
                if grid[i][j] == '1':
                    dfs(i, j)
                    res += 1
        return res
```