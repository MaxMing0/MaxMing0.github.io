---
layout:     post
title:      LeetCode 827 Making A Large Island (Python)
number:     827
level:      Hard
lcurl:      making-a-large-island
youtube:    QxSmKkJ74YM
bilibili1:  //player.bilibili.com/player.html?aid=504555176&bvid=BV1Cg4117727&cid=380863269&page=1
xigua:      
date:       2021-08-01
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - DFS
---

### 题目

You are given an n x n binary matrix grid. You are allowed to change at most one 0 to be 1.

Return the size of the largest island in grid after applying this operation.

An island is a 4-directionally connected group of 1s.

### 解题思路

首先求出每个岛的面积，给每个岛一个编号，存在字典里，之后枚举所有不是岛的位置，将四周所有相连的岛的面积加起来为能形成的岛的面积，注意一个位置与同一个岛多处相连

### 代码
```python
class Solution:
    def largestIsland(self, grid: List[List[int]]) -> int:
        def dfs(x, y, index):
            q = [(x, y)]
            visit = {(x, y)}
            while q:
                curx, cury = q.pop()
                grid[curx][cury] = index
                for dx, dy in directions:
                    tx, ty = curx + dx, cury + dy
                    if 0 <= tx < n and 0 <= ty < n and grid[tx][ty] == 1:
                        q.append((tx, ty))
                        visit.add((tx, ty))
            return len(visit)

        n = len(grid)
        directions = [(0, 1), (0, -1), (1, 0), (-1, 0)]
        area = {}
        index = 2
        for i in range(n):
            for j in range(n):
                if grid[i][j] == 1:
                    area[index] = dfs(i, j, index)
                    index += 1
        res = max(area.values() or [0])
        for i in range(n):
            for j in range(n):
                if grid[i][j] == 0:
                    tmp = set()
                    for dx, dy in directions:
                        tx, ty = i + dx, j + dy
                        if 0 <= tx < n and 0 <= ty < n and grid[tx][ty] > 1:
                            tmp.add(grid[tx][ty])
                    res = max(res, 1 + sum(area[t] for t in tmp))
        return res
```
