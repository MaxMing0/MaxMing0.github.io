---
layout:     post
title:      LeetCode 123 Best Time to Buy and Sell Stock III (Python)
number:     123
level:      Hard
lcurl:      best-time-to-buy-and-sell-stock-iii
youtube:    LFOn9_vHNA4
bilibili1:  //player.bilibili.com/player.html?aid=754253042&bvid=BV1rk4y117z8&cid=225118303&page=1
xigua:      
date:       2020-08-16
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - DP
---

### 题目

Say you have an array for which the ith element is the price of a given stock on day i.

Design an algorithm to find the maximum profit. You may complete at most two transactions.

Note: You may not engage in multiple transactions at the same time (i.e., you must sell the stock before you buy again).

### 解题思路

DP，因为只用考虑两次交易，所以在每一天只有四种状态，第一次买/卖，第二次买/卖，buy1,sell1,buy2,sell2分别为4种状态，因为只和前一天相关，所以可以只用4个变量滚动
```
buy1[i] = max(buy1[i - 1], -prices[i])
sell1[i] = max(sell1[i - 1], buy1[i] + prices[i])
buy2[i] = max(buy2[i - 1], sell1[i - 1] - prices[i])
sell2[i] = max(sell2[i - 1], buy2[i] + prices[i])
```

### 代码
```python
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        sell1 = sell2 = 0
        buy1 = buy2 = -float('inf')
        for p in prices:
            buy1 = max(buy1, -p);
            sell1 = max(sell1, buy1 + p)
            buy2 = max(buy2, sell1 - p)
            sell2 = max(sell2, buy2 + p)
        return sell2
```
