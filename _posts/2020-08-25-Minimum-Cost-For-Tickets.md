---
layout:     post
title:      LeetCode 983 Minimum Cost For Tickets (Python)
number:     983
level:      Medium
lcurl:      minimum-cost-for-tickets
youtube:    00UsGBgLgLI
bilibili1:  //player.bilibili.com/player.html?aid=584333159&bvid=BV1Wz4y1f7hG&cid=228696150&page=1
xigua:      
date:       2020-08-25
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - DP
---

### 题目

In a country popular for train travel, you have planned some train travelling one year in advance.  The days of the year that you will travel is given as an array days.  Each day is an integer from 1 to 365.

Train tickets are sold in 3 different ways:

- a 1-day pass is sold for costs[0] dollars;
- a 7-day pass is sold for costs[1] dollars;
- a 30-day pass is sold for costs[2] dollars.
The passes allow that many days of consecutive travel.  For example, if we get a 7-day pass on day 2, then we can travel for 7 days: day 2, 3, 4, 5, 6, 7, and 8.

Return the minimum number of dollars you need to travel every day in the given list of days.

### 解题思路

dp[i]表示车票覆盖到第i天的最小花费,dp[last_day]为所求
```
dp[0] = 0
dp[i] = min dp[i - 1] + costs[0] if i - 1 > 0
            dp[i - 7] + costs[1] if i - 7 > 0
            dp[i - 30] + costs[2] if i - 30 > 0
```

### 代码
```python
class Solution:
    def mincostTickets(self, days: List[int], costs: List[int]) -> int:
        first, last = days[0], days[-1]
        days = set(days)
        dp = [0] * (last + 1)
        for i in range(first, last + 1):
            if i in days:
                p1 = dp[i - 1] if i - 1 > 0 else 0
                p7 = dp[i - 7] if i - 7 > 0 else 0
                p30 = dp[i - 30] if i - 30 > 0 else 0
                dp[i] = min(p1 + costs[0], p7 + costs[1], p30 + costs[2])
            else:
                dp[i] = dp[i - 1]
        return dp[last]
```
