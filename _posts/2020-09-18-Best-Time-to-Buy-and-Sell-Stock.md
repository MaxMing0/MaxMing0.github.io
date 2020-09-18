---
layout:     post
title:      LeetCode 121 Best Time to Buy and Sell Stock (Python)
number:     121
level:      Easy
lcurl:      best-time-to-buy-and-sell-stock
youtube:    1r_0XLp6sSU
bilibili1:  //player.bilibili.com/player.html?aid=584719382&bvid=BV16z4y1Z7jD&cid=236509997&page=1
xigua:      
date:       2020-09-18
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Greedy
---

### 题目

Say you have an array for which the ith element is the price of a given stock on day i.

If you were only permitted to complete at most one transaction (i.e., buy one and sell one share of the stock), design an algorithm to find the maximum profit.

Note that you cannot sell a stock before you buy one.

### 解题思路

遍历价格的同时，记录当前的最低价，如果在当天卖出的最大收益就是当前价格减去最低价

### 代码
```python
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        res, cur_min = 0, float('inf')
        for p in prices:
            res = max(res, p - cur_min)
            cur_min = min(cur_min, p)
        return res
```
