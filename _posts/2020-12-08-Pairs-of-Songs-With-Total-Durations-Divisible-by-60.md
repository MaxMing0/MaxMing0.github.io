---
layout:     post
title:      LeetCode 1010 Pairs of Songs With Total Durations Divisible by 60 (Python)
number:     1010
level:      Medium
lcurl:      pairs-of-songs-with-total-durations-divisible-by-60
youtube:    SAzo0a2cj1c
bilibili1:  //player.bilibili.com/player.html?aid=755569034&bvid=BV1t64y1f7hc&cid=264308893&page=1
xigua:      
date:       2020-12-08
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - 
---

### 题目

You are given a list of songs where the ith song has a duration of time[i] seconds.

Return the number of pairs of songs for which their total duration in seconds is divisible by 60. Formally, we want the number of indices i, j such that i < j with (time[i] + time[j]) % 60 == 0.

### 解题思路

求出所有时间对60取余的出现的次数，i和60-i配对，0和30要单独处理

### 代码
```python
class Solution:
    def numPairsDivisibleBy60(self, time: List[int]) -> int:
        ct = Counter([t % 60 for t in time])
        res = 0
        res += ct[0] * (ct[0] - 1) // 2
        res += ct[30] * (ct[30] - 1) // 2
        res += sum([ct[i] * ct[60 - i] for i in range(1, 30)])
        return res
```
