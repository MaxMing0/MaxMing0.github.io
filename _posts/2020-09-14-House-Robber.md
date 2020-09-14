---
layout:     post
title:      LeetCode 198 House Robber (Python)
number:     198
level:      Easy
lcurl:      house-robber
youtube:    FDWFEETexhs
bilibili1:  //player.bilibili.com/player.html?aid=372073702&bvid=BV1gZ4y1N75c&cid=235273326&page=1
xigua:      
date:       2020-09-14
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - DP
---

### 题目

You are a professional robber planning to rob houses along a street. Each house has a certain amount of money stashed, the only constraint stopping you from robbing each of them is that adjacent houses have security system connected and it will automatically contact the police if two adjacent houses were broken into on the same night.

Given a list of non-negative integers representing the amount of money of each house, determine the maximum amount of money you can rob tonight without alerting the police.

### 解题思路

```
dp[i]表示打劫到第i个房子，最多能抢多少钱，dp[n]为所求
dp[i] = max(dp[i - 2] + nums[i], dp[i - 1])
dp[0] = nums[0]
dp[1] = max(nums[0], nums[1])
```

### 代码
```python
class Solution:
    def rob(self, nums: List[int]) -> int:
        dp0 = dp1 = 0
        for i in range(len(nums)):
            dp0, dp1 = dp1, max(dp0 + nums[i], dp1)
        return dp1
```
