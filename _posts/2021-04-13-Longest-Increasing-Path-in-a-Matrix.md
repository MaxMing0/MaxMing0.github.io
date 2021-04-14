---
layout:     post
title:      LeetCode 329 Longest Increasing Path in a Matrix (Python)
number:     329
level:      Medium
lcurl:      longest-increasing-path-in-a-matrix
youtube:    aDle1bqPQ5Q
bilibili1:  //player.bilibili.com/player.html?aid=887539788&bvid=BV1VK4y1K7SX&cid=323917196&page=1
xigua:      
date:       2021-04-13
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - 
---

### 题目

Given an m x n integers matrix, return the length of the longest increasing path in matrix.

From each cell, you can either move in four directions: left, right, up, or down. You may not move diagonally or move outside the boundary (i.e., wrap-around is not allowed).

### 解题思路

dp，使用memorization，dp[x][y] = 1 + max(dp[x - 1][y], dp[x + 1][y], dp[x][y - 1], dp[x][y + 1])

### 代码
```python
class Solution:
    def longestIncreasingPath(self, matrix: List[List[int]]) -> int:
        @lru_cache(None)
        def dp(x, y):
            val = matrix[x][y]
            ret = 1 + max(
                dp(x - 1, y) if x > 0 and val > matrix[x - 1][y] else 0,
                dp(x + 1, y) if x < m - 1 and val > matrix[x + 1][y] else 0,
                dp(x, y - 1) if y > 0 and val > matrix[x][y - 1] else 0,
                dp(x, y + 1) if y < n - 1 and val > matrix[x][y + 1] else 0)
            return ret

        m, n = len(matrix), len(matrix[0])
        return max(dp(x, y) for x in range(m) for y in range(n))
```
