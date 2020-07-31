---
layout:     post
title:      LeetCode 70 Climbing Stairs (Python)
number:     70
level:      Easy
lcurl:      climbing-stairs
youtube:    fXewpNXwWBU
bilibili1:  //player.bilibili.com/player.html?aid=541602869&bvid=BV1ki4y1u7tn&cid=218760127&page=1
xigua:      
date:       2020-07-31
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - DP
---

### 题目

You are climbing a stair case. It takes n steps to reach to the top.

Each time you can either climb 1 or 2 steps. In how many distinct ways can you climb to the top?

### 解题思路

dp, `dp[i]=dp[i-1]+dp[i-2]`，因为到第n级台阶，可以由n-1或者n-2级台阶走到

### 代码
```python
class Solution:
    def climbStairs(self, n: int) -> int:
        dp1, dp2 = 1, 2
        for i in range(n - 1):
            dp1, dp2 = dp2, dp1 + dp2
        return dp1
```
