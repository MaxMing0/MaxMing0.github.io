---
layout:     post
title:      LeetCode 63 Unique Paths II (Python)
number:     63
level:      Medium
lcurl:      unique-paths-ii
youtube:    lmVgprB6Mj0
bilibili1:  //player.bilibili.com/player.html?aid=247820378&bvid=BV1Sv411L7qe&cid=330815331&page=1
xigua:      
date:       2021-04-28
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - DP
---

### 题目

A robot is located at the top-left corner of a m x n grid (marked 'Start' in the diagram below).

The robot can only move either down or right at any point in time. The robot is trying to reach the bottom-right corner of the grid (marked 'Finish' in the diagram below).

Now consider if some obstacles are added to the grids. How many unique paths would there be?

An obstacle and space is marked as 1 and 0 respectively in the grid.

### 解题思路

每个格子的路径数为上左两个路径之和，如果格子为障碍物，路径为0

### 代码
```python
class Solution:
    def uniquePathsWithObstacles(self, obstacleGrid: List[List[int]]) -> int:
        m, n = len(obstacleGrid), len(obstacleGrid[0])
        if obstacleGrid[m - 1][n - 1] == 1 or obstacleGrid[0][0] == 1:
            return 0
        obstacleGrid[0][0] = 1
        for i in range(1, m):
            obstacleGrid[i][0] = 0 if obstacleGrid[i][0] else obstacleGrid[i - 1][0]
        for i in range(1, n):
            obstacleGrid[0][i] = 0 if obstacleGrid[0][i] else obstacleGrid[0][i - 1]
        for i in range(1, m):
            for j in range(1, n):
                obstacleGrid[i][j] = 0 if obstacleGrid[i][j] else obstacleGrid[i][j - 1] + obstacleGrid[i - 1][j]
        return obstacleGrid[m - 1][n - 1]
```
