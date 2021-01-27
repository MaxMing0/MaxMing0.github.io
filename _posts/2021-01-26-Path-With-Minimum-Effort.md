---
layout:     post
title:      LeetCode 1631 Path With Minimum Effort (Python)
number:     1631
level:      Medium
lcurl:      path-with-minimum-effort
youtube:    Eqj9XJaZ6W4
bilibili1:  //player.bilibili.com/player.html?aid=628781556&bvid=BV1ft4y1z71X&cid=288218679&page=1
xigua:      
date:       2021-01-26
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Graph
---

### 题目

You are a hiker preparing for an upcoming hike. You are given heights, a 2D array of size rows x columns, where heights[row][col] represents the height of cell (row, col). You are situated in the top-left cell, (0, 0), and you hope to travel to the bottom-right cell, (rows-1, columns-1) (i.e., 0-indexed). You can move up, down, left, or right, and you wish to find a route that requires the minimum effort.

A route's effort is the maximum absolute difference in heights between two consecutive cells of the route.

Return the minimum effort required to travel from the top-left cell to the bottom-right cell.

### 解题思路

Dijkstra，把距离改为从（0，0）到当前位置的最大effort

### 代码
```python
class Solution:
    def minimumEffortPath(self, heights) -> int:
        m, n = len(heights), len(heights[0])
        distances = defaultdict(lambda: float('inf'))
        dirs = [(0, 1), (1, 0), (0, -1), (-1, 0)]
        q = []
        heappush(q, (0, 0, 0))
        while q:
            effort, curx, cury = heappop(q)
            if (curx, cury) == (m - 1, n - 1):
                return effort
            for dx, dy in dirs:
                tx, ty = curx + dx, cury + dy
                if 0 <= tx < m and 0 <= ty < n:
                    tmp = max(effort, abs(heights[tx][ty] - heights[curx][cury]))
                    if distances[(tx, ty)] > tmp:
                        distances[(tx, ty)] = tmp
                        heappush(q, (tmp, tx, ty))
```
