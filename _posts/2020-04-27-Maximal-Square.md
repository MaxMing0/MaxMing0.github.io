---
layout:     post
title:      LeetCode 221 Maximal Square (Python)
number:     221
level:      Medium
lcurl:      maximal-square
youtube:    q1hb3tGzoZM
bilibili1:  //player.bilibili.com/player.html?aid=497980859&bvid=BV16K411575r&cid=183951287&page=1
xigua:      
date:       2020-04-27
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - DP
---

### 题目

Given a 2D binary matrix filled with 0's and 1's, find the largest square containing only 1's and return its area.

### 解题思路
```
dp[i][j] = min(dp[i - 1][j - 1], dp[i][j - 1], dp[i - 1][j]) + 1 if dp[i - 1][j - 1] == 1
         = 0 else
```
### 代码
```python
class Solution:
    def maximalSquare(self, matrix: List[List[str]]) -> int:
        m = len(matrix)
        if m == 0:
            return 0
        n = len(matrix[0])
        if n == 0:
            return 0
        res = 0
        dp1 = [0] * (n + 1)
        dp2 = [0] * (n + 1)
        for i in range(1, m + 1):
            for j in range(1, n + 1):
                if matrix[i - 1][j - 1] == "1":
                    dp2[j] = min(dp1[j - 1], dp1[j], dp2[j - 1]) + 1
                    res = max(res, dp2[j])
                else:
                    dp2[j] = 0
            dp1 = dp2[:]
        return res * res
```
