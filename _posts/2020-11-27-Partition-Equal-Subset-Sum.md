---
layout:     post
title:      LeetCode 416 Partition Equal Subset Sum (Python)
number:     416
level:      Medium
lcurl:      partition-equal-subset-sum
youtube:    yrD853oXwOw
bilibili1:  //player.bilibili.com/player.html?aid=712976957&bvid=BV1DD4y1X7Cp&cid=260279967&page=1
xigua:      
date:       2020-11-27
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - DP
---

### 题目

Given a non-empty array nums containing only positive integers, find if the array can be partitioned into two subsets such that the sum of elements in both subsets is equal.

### 解题思路

```
dp[i][j]表示从nums[0]..nums[i]这些数中，取若干个数(可以为0)，能否构成j，dp[n-1][target]为所求
dp[i][j] = dp[i-1][j] | dp[i-1][j-nums[i]] (j >= nums[i])
dp[i][0] = True
dp[0][nums[0]] = True
使用一维数组：
dp[j] = dp[j] | dp[j - nums[i]]
```

### 代码
```python
class Solution:
    def canPartition(self, nums: List[int]) -> bool:
        if len(nums) < 2:
            return False
        total = sum(nums)
        if total % 2 != 0:
            return False
        target = total // 2
        dp = [True] + [False] * target
        for i, n in enumerate(nums):
            for j in range(target, n - 1, -1):
                dp[j] |= dp[j - n]
        return dp[target]
```
