---
layout:     post
title:      LeetCode 309 Best Time to Buy and Sell Stock with Cooldown (Python)
number:     209
level:      Medium
lcurl:      best-time-to-buy-and-sell-stock-with-cooldown
youtube:    VwRFvazWkaw
bilibili1:  //player.bilibili.com/player.html?aid=711574954&bvid=BV13D4y1U7iU&cid=217968445&page=1
xigua:      
date:       2020-07-29
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - DP
---

### 题目

Say you have an array for which the ith element is the price of a given stock on day i.

Design an algorithm to find the maximum profit. You may complete as many transactions as you like (ie, buy one and sell one share of the stock multiple times) with the following restrictions:

- You may not engage in multiple transactions at the same time (ie, you must sell the stock before you buy again).
- After you sell your stock, you cannot buy stock on next day. (ie, cooldown 1 day)

### 解题思路

动态规划，设f[i]表示在第i天结束之后的最大收益，有三种情况，f[i][0]表示持有股票，f[i][1]表示第i天卖了股票，处于冷冻期，f[i][2]表示没有持有股票，且不处于冷冻期,max(f[n-1])为所求
```
f[i][0] = max(f[i-1][0], f[i-1][2]-prices[i])
f[i][1] = f[i-1][1] + prices[i]
f[i][2] = max(f[i-1][1], f[i-1][2])
f[0][0] = -prices[0]
f[0][1] = f[0][2] = 0
```

### 代码
```python
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        if not prices:
            return 0
        f0, f1, f2 = -prices[0], 0, 0
        for i in range(1, len(prices)):
            t0 = max(f0, f2 - prices[i])
            t1 = f0 + prices[i]
            f2 = max(f1, f2)
            f0, f1 = t0, t1
        return max(f1, f2)
```
