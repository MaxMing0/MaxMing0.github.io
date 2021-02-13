---
layout:     post
title:      LeetCode 1091 Shortest Path in Binary Matrix (Python)
number:     1091
level:      Medium
lcurl:      shortest-path-in-binary-matrix
youtube:    CHzWNewmlqo
bilibili1:  //player.bilibili.com/player.html?aid=374191570&bvid=BV1ro4y197kU&cid=297163344&page=1
xigua:      
date:       2021-02-13
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - BFS
---

### 题目

In an N by N square grid, each cell is either empty (0) or blocked (1).

A clear path from top-left to bottom-right has length k if and only if it is composed of cells C_1, C_2, ..., C_k such that:

Adjacent cells C_i and C_{i+1} are connected 8-directionally (ie., they are different and share an edge or corner)
- C_1 is at location (0, 0) (ie. has value grid[0][0])
- C_k is at location (N-1, N-1) (ie. has value grid[N-1][N-1])
- If C_i is located at (r, c), then grid[r][c] is empty (ie. grid[r][c] == 0).
Return the length of the shortest such clear path from top-left to bottom-right.  If such a path does not exist, return -1.

### 解题思路

标准的BFS求最短路，注意起始的两个格可能是1

### 代码
```python
class Solution:
    def shortestPathBinaryMatrix(self, grid: List[List[int]]) -> int:
        n = len(grid)
        if grid[0][0] or grid[n - 1][n - 1]:
            return -1
        directions = [(-1, -1), (-1, 0), (-1, 1), (0, -1), (0, 1), (1, -1), (1, 0), (1, 1)]
        q = deque([(0, 0, 1)])
        visit = {(0, 0)}
        while q:
            curx, cury, curd = q.popleft()
            if curx == cury == n - 1:
                    return curd
            for dx, dy in directions:
                tx, ty = curx + dx, cury + dy
                if (tx, ty) not in visit and 0 <= tx < n and 0 <= ty < n and grid[tx][ty] == 0:
                    visit.add((tx, ty))
                    q.append((tx, ty, curd + 1))
        return -1
```
