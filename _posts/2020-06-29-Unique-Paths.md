---
layout:     post
title:      LeetCode 62 Unique Paths (Python)
number:     62
level:      Medium
lcurl:      unique-paths
youtube:    3UrAVgNb94o
bilibili1:  //player.bilibili.com/player.html?aid=838736859&bvid=BV1Sg4y1v7PM&cid=207086799&page=1
xigua:      
date:       2020-06-29
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - DP
    - Math
---

### 题目

A robot is located at the top-left corner of a m x n grid (marked 'Start' in the diagram below).

The robot can only move either down or right at any point in time. The robot is trying to reach the bottom-right corner of the grid (marked 'Finish' in the diagram below).

How many possible unique paths are there?

### 解题思路

1. 数学方法，m*n的方格一共需要走`m+n-2`步，其中`m-1`步向下，一共走法是组合数C(m+n-2,m-1)
2. 动态规划，dp[i][j]表示走到(i,j)的走法数，dp[i][j] = dp[i-1][j] + dp[i][j-1]

### 代码
```python
class Solution:
    def uniquePaths(self, m: int, n: int) -> int:
        // return math.factorial(m + n - 2) // math.factorial(m - 1) // math.factorial(n - 1)
        return math.comb(m + n - 2, m - 1)
```

```python
class Solution:
    def uniquePaths(self, m: int, n: int) -> int:
        dp = [1] * n
        for i in range(1, m):
            for j in range(1, n):
                dp[j] += dp[j - 1]
        return dp[-1]
```
