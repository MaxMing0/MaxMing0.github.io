---
layout:     post
title:      LeetCode 1143 Longest Common Subsequence (Python)
number:     1143
level:      Medium
lcurl:      longest-common-subsequence
youtube:    Wt0KdgvYfjc
bilibili1:  //player.bilibili.com/player.html?aid=370451362&bvid=BV19Z4y1W7Xi&cid=183522840&page=1
xigua:      
date:       2020-04-26
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - DP
---

### 题目

Given two strings text1 and text2, return the length of their longest common subsequence.

A subsequence of a string is a new string generated from the original string with some characters(can be none) deleted without changing the relative order of the remaining characters. (eg, "ace" is a subsequence of "abcde" while "aec" is not). A common subsequence of two strings is a subsequence that is common to both strings.

If there is no common subsequence, return 0.

### 解题思路
dp[i][j] = 0 if i == 0 or j == 0
         = dp[i - 1][j - 1] + 1 if text1[i] == text2[j]
         = max(dp[i - 1][j], dp[i][j - 1]) else


### 代码
```python
class Solution:
    def longestCommonSubsequence(self, text1: str, text2: str) -> int:
        l1, l2 = len(text1), len(text2)
        #dp = [[0] * (l2 + 1) for _ in range(l1 + 1)]
        dp1 = [0] * (l2 + 1)
        dp2 = [0] * (l2 + 1)
        for i in range(1, l1 + 1):
            for j in range(1, l2 + 1):
                if text1[i - 1] == text2[j - 1]:
                    # dp[i][j] = dp[i - 1][j - 1] + 1
                    dp2[j] = dp1[j - 1] + 1
                else:
                    # dp[i][j] = max(dp[i - 1][j], dp[i][j - 1])
                    dp2[j] = max(dp1[j], dp2[j - 1])
            dp1 = dp2[:]
        return dp1[-1]
```