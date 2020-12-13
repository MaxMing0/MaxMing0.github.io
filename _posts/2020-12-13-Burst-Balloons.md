---
layout:     post
title:      LeetCode 312 Burst Balloons (Python)
number:     312
level:      Hard
lcurl:      burst-balloons
youtube:    D0lIy0bq0YE
bilibili1:  //player.bilibili.com/player.html?aid=755682054&bvid=BV1Q64y1f7Vy&cid=266228477&page=1
xigua:      
date:       2020-12-13
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - DP
---

### 题目

Given n balloons, indexed from 0 to n-1. Each balloon is painted with a number on it represented by array nums. You are asked to burst all the balloons. If the you burst balloon i you will get nums[left] * nums[i] * nums[right] coins. Here left and right are adjacent indices of i. After the burst, the left and right then becomes adjacent.

Find the maximum coins you can collect by bursting the balloons wisely.

Note:

- You may imagine nums[-1] = nums[n] = 1. They are not real therefore you can not burst them.
- 0 ≤ n ≤ 500, 0 ≤ nums[i] ≤ 100

### 解题思路
```nums = [1] + nums + [1], dp[i][j]表示在i，j开区间，插满气球可以获得的最优值，dp[0][n - 1]为所求
dp[i][j] = max(nums[i] * nums[k] * nums[j] + dp[i][k] + dp[k][j]) for k in (i + 1, j) if i + 1 < j
         = 0 i + 1 >= j
```

### 代码
```python
class Solution:
    def maxCoins(self, nums: List[int]) -> int:
        nums = [1] + nums + [1]
        n = len(nums)
        dp = [[0] * n for _ in range(n)]
        for i in range(n - 2, -1, -1):
            for j in range(i + 2, n):
                for k in range(i + 1, j):
                    dp[i][j] = max(dp[i][j], nums[i] * nums[k] * nums[j] + dp[i][k] + dp[k][j])
        return dp[0][n - 1]
```
```python
class Solution:
    def maxCoins(self, nums: List[int]) -> int:
        def dp(i, j):
            if i + 1 == j:
                data[i][j] = 0
                return 0
            tmp = 0
            for k in range(i + 1, j):
                if data[i][k] == -1:
                    dp(i, k)
                if data[k][j] == -1:
                    dp(k, j)
                tmp = max(tmp, nums[i] * nums[k] * nums[j] + data[i][k] + data[k][j])
            data[i][j] = tmp
            return tmp
        
        nums = [1] + nums + [1]
        n = len(nums)
        data = [[-1]  * n for i in range(n)]
        return dp(0, n - 1)
```
