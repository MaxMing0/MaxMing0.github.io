---
layout:     post
title:      LeetCode 64 Minimum Path Sum (Python)
number:     64
level:      Medium
lcurl:      minimum-path-sum
youtube:    xUz7y_Enq7A
bilibili1:  //player.bilibili.com/player.html?aid=795344827&bvid=BV1JC4y1x7j1&cid=180033160&page=1
xigua:      
date:       2020-04-26
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - DP
---

### 题目

Given a m x n grid filled with non-negative numbers, find a path from top left to bottom right which minimizes the sum of all numbers along its path.

Note: You can only move either down or right at any point in time.

### 解题思路

动态规划，每个格子可以从它上方或者左边的格子走到，所以走到这个格子的最小和就是上边和左边的两个和取较小者，并加上当前的数值

第一行的每个格子，只能从左边走到，第一列的每个格子，只能从上边走到
```
dp[i][j] = dp[0][j - 1] + grid[i][j] if i = 0
         = dp[i - 1][0] + grid[i][j] if j = 0
         = min(dp[i - 1][j], dp[i][j - 1]) + grid[i][j]
```

### 代码
```python
class Solution:
    def minPathSum(self, grid: List[List[int]]) -> int:
        m, n = len(grid), len(grid[0])
        for i in range(1, n):
            grid[0][i] += grid[0][i - 1]
        for i in range(1, m):
            grid[i][0] += grid[i - 1][0]
            for j in range(1, n):
                grid[i][j] += min(grid[i - 1][j], grid[i][j - 1])
        return grid[m - 1][n - 1]
```
