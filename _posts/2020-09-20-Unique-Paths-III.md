---
layout:     post
title:      LeetCode 980 Unique Paths III (Python)
number:     980
level:      Hard
lcurl:      unique-paths-iii
youtube:    kkr2O9Hy7fs
bilibili1:  //player.bilibili.com/player.html?aid=884692581&bvid=BV1oK4y1a7Qp&cid=237406164&page=1
xigua:      
date:       2020-09-20
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Backtracking
---

### 题目

On a 2-dimensional grid, there are 4 types of squares:

- 1 represents the starting square.  There is exactly one starting square.
- 2 represents the ending square.  There is exactly one ending square.
- 0 represents empty squares we can walk over.
- -1 represents obstacles that we cannot walk over.
Return the number of 4-directional walks from the starting square to the ending square, that walk over every non-obstacle square exactly once.

### 解题思路

回溯，首先遍历整个矩阵，找到起始位置，以及统计空格子的个数，之后向四个方向进行dfs，同时传入还省多少格子要走，标记走过的格子，如果走到中点，并且所有格子已经走过，则是一条路径

### 代码
```python
class Solution:
    def uniquePathsIII(self, grid: List[List[int]]) -> int:
        startx = starty = empty = 0
        for row in range(0, len(grid)):
            for col in range(0, len(grid[0])):
                cell = grid[row][col] 
                if cell >= 0:
                    empty += 1
                if cell == 1:
                    startx, starty = row, col
        return self.dfs(grid, startx, starty, empty)
        
    def dfs(self, grid, x, y, step):
        if grid[x][y] == 2: 
            return step == 1
        ret = 0
        cur = grid[x][y]
        grid[x][y] = -2
        for dirx, diry in [(0, 1), (1, 0), (0, -1), (-1, 0)]:
            tx, ty = x + dirx, y + diry
            if 0 <= tx < len(grid) and 0 <= ty < len(grid[0]) and grid[tx][ty] >= 0:
                ret += self.dfs(grid, tx, ty, step - 1)
        grid[x][y] = cur
        return ret
```
