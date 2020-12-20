---
layout:     post
title:      LeetCode 1463 Cherry Pickup II (Python)
number:     1463
level:      Hard
lcurl:      cherry-pickup-ii
youtube:    khgVp9oa9No
bilibili1:  //player.bilibili.com/player.html?aid=330625064&bvid=BV1AA411s7Tc&cid=268509226&page=1
xigua:      
date:       2020-12-19
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - DP
---

### 题目

Given a rows x cols matrix grid representing a field of cherries. Each cell in grid represents the number of cherries that you can collect.

You have two robots that can collect cherries for you, Robot #1 is located at the top-left corner (0,0) , and Robot #2 is located at the top-right corner (0, cols-1) of the grid.

Return the maximum number of cherries collection using both robots  by following the rules below:

- From a cell (i,j), robots can move to cell (i+1, j-1) , (i+1, j) or (i+1, j+1).
- When any robot is passing through a cell, It picks it up all cherries, and the cell becomes an empty cell (0).
- When both robots stay on the same cell, only one of them takes the cherries.
- Both robots cannot move outside of the grid at any moment.
- Both robots should reach the bottom row in the grid.

### 解题思路

```
dp[i][j1][j2]表示从第i行，一个机器人在j1位置，一个在j2位置，走到最后一行可以拿到的最大值，dp[0][0][n-1]为所求
dp[i][j1][j2] = max(dp[i+1][d1][d2]) + grid[i][j1] + grid[j][j2]
    d1 = [j1-1, j1, j1+1]
    d2 = [j2-1, j2, j2+1]
    0 <= d1, d2 < n
    d1 < d2 （通过保持让左边的机器人一直在左边，进行优化）

边界：dp[m-1][j1][j2] = grid[m-1][j1] + grid[m-1][j2]
```

### 代码
```python
class Solution:
    def cherryPickup(self, grid: List[List[int]]) -> int:
        @lru_cache(None)
        def dfs(i, j1, j2):
            if i == m - 1:
                return grid[i][j1] + grid[i][j2]
            ret = 0
            for d1 in [j1 - 1, j1, j1 + 1]:
                for d2 in [j2 - 1, j2, j2 + 1]:
                    if d1 < d2 and 0 <= d1 < n and 0 <= d2 < n:
                        ret = max(ret, dfs(i + 1, d1, d2))
            return ret + grid[i][j1] + grid[i][j2]
        
        m, n = len(grid), len(grid[0])
        return dfs(0, 0, n - 1)
```
