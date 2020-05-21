---
layout:     post
title:      LeetCode 1277 Count Square Submatrices with All Ones (Python)
number:     1227
level:      Medium
lcurl:      https://leetcode.com/problems/count-square-submatrices-with-all-ones
youtube:    UrpCGoljrQI
bilibili1:  //player.bilibili.com/player.html?aid=968270057&bvid=BV1Kp4y1X7n4&cid=193564195&page=1
xigua:      
date:       2020-05-21
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - DP
---

### 题目

Given a m * n matrix of ones and zeros, return how many square submatrices have all ones.

### 解题思路

DP, dp[i][j]表示以（i，j）为右下角的正方形的个数，dp数组的总和即为所求
```
dp[i][j] = min(dp[i - 1][j - 1], dp[i][j - 1], dp[i - 1][j]) + 1 if dp[i - 1][j - 1] == 1
         = 0 else
```

### 代码
```python
class Solution:
    def countSquares(self, matrix: List[List[int]]) -> int:
        m, n = len(matrix), len(matrix[0])
        dp = [matrix[0][i] for i in range(n)]
        res = sum(dp)
        for i in range(1, m):
            tmp = [matrix[i][0]]
            for j in range(1, n):
                if matrix[i][j]:
                    tmp.append(min(tmp[-1], dp[j], dp[j - 1]) + 1)
                else:
                    tmp.append(0)
            res += sum(tmp)
            dp = tmp[:]
        return res
```
