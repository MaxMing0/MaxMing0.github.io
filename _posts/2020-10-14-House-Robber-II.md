---
layout:     post
title:      LeetCode 213 House Robber II (Python)
number:     213
level:      Medium
lcurl:      house-robber-ii
youtube:    Cf7VyZU-zuY
bilibili1:  //player.bilibili.com/player.html?aid=712391681&bvid=BV1GD4y1d7DS&cid=245567173&page=1
xigua:      
date:       2020-10-14
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - DP
---

### 题目

You are a professional robber planning to rob houses along a street. Each house has a certain amount of money stashed. All houses at this place are arranged in a circle. That means the first house is the neighbor of the last one. Meanwhile, adjacent houses have a security system connected, and it will automatically contact the police if two adjacent houses were broken into on the same night.

Given a list of non-negative integers nums representing the amount of money of each house, return the maximum amount of money you can rob tonight without alerting the police.

### 解题思路

使用House Robber I的做法，[链接](https://maxming0.github.io/2020/09/14/House-Robber/)

对于这道题，我们可以把环拆成0到n-1和1到n的两个链，做两次dp去最大值

### 代码
```python
class Solution:
    def _rob(self, nums: List[int]) -> int:
        dp0 = dp1 = 0
        for i in range(len(nums)):
            dp0, dp1 = dp1, max(dp0 + nums[i], dp1)
        return dp1
    
    def rob(self, nums: List[int]) -> int:
        if len(nums) == 1:
            return nums[0]
        return max(self._rob(nums[:-1]), self._rob(nums[1:]))
```
