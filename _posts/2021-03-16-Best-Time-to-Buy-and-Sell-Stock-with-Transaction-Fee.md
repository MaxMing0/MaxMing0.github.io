---
layout:     post
title:      LeetCode 714 Best Time to Buy and Sell Stock with Transaction Fee (Python)
number:     714
level:      Medium
lcurl:      best-time-to-buy-and-sell-stock-with-transaction-fee
youtube:    ai6gbASEMBE
bilibili1:  //player.bilibili.com/player.html?aid=844714952&bvid=BV1t54y187Qy&cid=311099115&page=1
xigua:      
date:       2021-03-16
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - DP
---

### 题目

You are given an array prices where prices[i] is the price of a given stock on the ith day, and an integer fee representing a transaction fee.

Find the maximum profit you can achieve. You may complete as many transactions as you like, but you need to pay the transaction fee for each transaction.

Note: You may not engage in multiple transactions simultaneously (i.e., you must sell the stock before you buy again).

### 解题思路

```
cash[i]表示在第i天结束之后，没股票的最大值
hold[i]表示在第i天结束之后，持有股票的最大值
cash[i] = max(cash[i - 1], hold[i - 1] + price[i] - fee)
hold[i] = max(hold[i - 1], cash - price[i])
cash[0] = 0
hold[i] = -price[0]
dp数组可以只用一个变量表示
```

### 代码
```python
class Solution:
    def maxProfit(self, prices: List[int], fee: int) -> int:
        cash, hold = 0, -prices[0]
        for i in range(1, len(prices)):
            cash = max(cash, hold + prices[i] - fee)
            hold = max(hold, cash - prices[i])
        return cash
```
