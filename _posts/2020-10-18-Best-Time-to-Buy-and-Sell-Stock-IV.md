---
layout:     post
title:      LeetCode LeetCode 每日一题 Daily Challenge 188 Best Time to Buy and Sell Stock IV (Python)
number:     188
level:      Hard
lcurl:      best-time-to-buy-and-sell-stock-iv
youtube:    aNoSpLIoB-k
bilibili1:  //player.bilibili.com/player.html?aid=842405058&bvid=BV1f54y1k7cX&cid=246983222&page=1
xigua:      
date:       2020-10-18
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - DP
    - Greedy
---

### 题目

You are given an integer array prices where prices[i] is the price of a given stock on the ith day.

Design an algorithm to find the maximum profit. You may complete at most k transactions.

Notice that you may not engage in multiple transactions simultaneously (i.e., you must sell the stock before you buy again).

### 解题思路
如果k大于n/2，就变成第122题[LeetCode122解答](https://maxming0.github.io/2020/04/26/Best-Time-to-Buy-and-Sell-Stock-II/),同时也推荐先看第123题，只能进行两次交易的简化版[LeetCode123解答](https://maxming0.github.io/2020/08/16/Best-Time-to-Buy-and-Sell-Stock-III/)
```
dp[i][0][1] 第一次买入
dp[i][1][0] 第一次卖出。

dp[i][j-1][1]：表示第i天，第j次买入后的累计最大利润
dp[i][j][0]：表示第i天，第j次卖出后的累计最大利润
dp[i][0][0] = 0

第j次买入： 第j次买入后保持不动 从第j-1次卖出后买入
dp[i][j-1][1] = max(dp[i-1][j-1][1], dp[i-1][j-1][0] - prices[i])

第j次卖出： 第j次卖出后保持不动 第j次买入后卖出
dp[i][j][0] = max(dp[i-1][j][0], dp[i-1][j-1][1] + prices[i])

因为第j次买入只和第j-1卖出相关，第j次卖出只和第j次买入相关，所以可以省去第一维
dp[j-1][1] = max(dp[j-1][1], dp[j-1][0] - prices[i])
dp[j][0] = max(dp[j][0], dp[j-1][1] + prices[i])
```

### 代码
```python
class Solution:
    def maxProfit(self, k: int, prices: List[int]) -> int:
        if not prices:
            return 0
        n = len(prices)
        if k > n // 2:
            res = 0
            for i in range(1, len(prices)):
                if prices[i] > prices[i - 1]:
                    res += prices[i] - prices[i - 1]
            return res
        
        n = len(prices)
        dp = [[0, 0] for _ in range(k + 1)]
        for i in range(k + 1):
            dp[i][1] = -prices[0]
        for i in range(1, n):
            for j in range(1, k + 1):
                dp[j - 1][1] = max(dp[j - 1][1], dp[j - 1][0] - prices[i])
                dp[j][0] = max(dp[j][0], dp[j - 1][1] + prices[i])  
        return dp[k][0]
```
