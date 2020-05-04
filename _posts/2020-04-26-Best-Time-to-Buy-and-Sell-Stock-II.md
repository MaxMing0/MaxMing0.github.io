---
layout:     post
title:      LeetCode 122 Best Time to Buy and Sell Stock II (Python)
number:     122
level:      Easy
lcurl:      best-time-to-buy-and-sell-stock-ii
youtube:    bx1ZHsH9mmM
bilibili1:  //player.bilibili.com/player.html?aid=752689622&bvid=BV1Fk4y1R7ve&cid=174270712&page=1
xigua:      
date:       2020-04-26
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Greedy
---

### 题目

Say you have an array prices for which the ith element is the price of a given stock on day i.

Design an algorithm to find the maximum profit. You may complete as many transactions as you like (i.e., buy one and sell one share of the stock multiple times).

Note: You may not engage in multiple transactions at the same time (i.e., you must sell the stock before you buy again).

### 解题思路

贪心，如果某天的股价比前一天的高，那么就在前一天买入，并在当天卖出，不需要找每次的高点和低点

### 代码
```python
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        res = 0
        for i in range(1, len(prices)):
            if prices[i] > prices[i - 1]:
                res += prices[i] - prices[i - 1]
        return res
```
