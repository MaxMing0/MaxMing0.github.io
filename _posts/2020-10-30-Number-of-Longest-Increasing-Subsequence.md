---
layout:     post
title:      LeetCode 673 Number of Longest Increasing Subsequence (Python)
number:     673
level:      Medium
lcurl:      number-of-longest-increasing-subsequence
youtube:    BWWVRPoDjDA
bilibili1:  //player.bilibili.com/player.html?aid=927555802&bvid=BV1gT4y1F7y3&cid=250921742&page=1
xigua:      
date:       2020-10-30
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - DP
---

### 题目

Given an integer array nums, return the number of longest increasing subsequences.

### 解题思路

首先做第300题，最长递升子序列
```
对于这道题统计个数，设dp[i][j]表示长度为i，以j为结尾的最长递升子序列的个数
dp[i][n] += sum(dp[i - 1][j] for j in dp[i - 1] if j < n)
dp[0][-inf] = 1
sum(dp[length])为所求
其中i为最长递升子序列二分得到的插入点（以当前数字n为结尾的最长子序列的长度）
```

### 代码
```python
class Solution:
    def findNumberOfLIS(self, nums):
        dp = collections.defaultdict(collections.Counter)
        dp[-1][float('-inf')] = 1
        table = []
        for n in nums:
            i = bisect.bisect_left(table, n)
            if i == len(table):
                table.append(n)
            else:
                table[i] = n
            dp[i][n] += sum(dp[i - 1][j] for j in dp[i - 1] if j < n)
        return sum(dp[max(0, len(table) - 1)].values())
```
