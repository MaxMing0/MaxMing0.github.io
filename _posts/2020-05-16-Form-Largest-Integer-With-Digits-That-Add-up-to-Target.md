---
layout:     post
title:      LeetCode 1449 Form Largest Integer With Digits That Add up to Target (Python)
number:     1449
level:      Hard
lcurl:      form-largest-integer-with-digits-that-add-up-to-target
youtube:    I0Ttr25Nio4
bilibili1:  //player.bilibili.com/player.html?aid=840719054&bvid=BV1j54y1D7vf&cid=191928105&page=1
xigua:      
date:       2020-05-16
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - DP
---

### 题目

Given an array of integers cost and an integer target. Return the maximum integer you can paint under the following rules:

- The cost of painting a digit (i+1) is given by cost[i] (0 indexed).
- The total cost used must be equal to target.
- Integer does not have digits 0.

Since the answer may be too large, return it as string.

If there is no way to paint any integer given the condition, return "0".

### 解题思路

DP，是一个标准的背包问题，dp[t]表示花费t能构成的最大数，dp[target]为结果
```
dp[t] = max(dp[t - cost] * 10 + number if t - cost >= 0)
dp[0] = 0
```

### 代码
```python
class Solution:
    def largestNumber(self, cost: List[int], target: int) -> str:
        dp = [0] + [-1] * (target)
        for t in range(1, target + 1):
            for i, c in enumerate(cost):
                if t - c >= 0:
                    dp[t] = max(dp[t], dp[t - c] * 10 + i + 1)
        return str(max(dp[target], 0))
```
