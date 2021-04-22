---
layout:     post
title:      LeetCode 377 Combination Sum IV (Python)
number:     377
level:      Medium
lcurl:      combination-sum-iv
youtube:    7OpV-bit978
bilibili1:  //player.bilibili.com/player.html?aid=332631210&bvid=BV1zA411L7nu&cid=327533461&page=1
xigua:      
date:       2021-04-21
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - DP
---

### 题目

Given an array of distinct integers nums and a target integer target, return the number of possible combinations that add up to target.

The answer is guaranteed to fit in a 32-bit integer.

### 解题思路

dp[i]表示构成i有多少种方法，dp[target]为所求
dp[i] = sum(dp[i - n]) for n in nums if n <= i
dp[0] = 1

### 代码
```python
class Solution:
    def combinationSum4(self, nums: List[int], target: int) -> int:
        dp = [1]
        for i in range(1, target + 1):
            dp.append(sum([dp[i - n] for n in nums if n <= i]))
        return dp[target]
```
