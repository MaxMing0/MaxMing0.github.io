---
layout:     post
title:      LeetCode 495 Teemo Attacking (Python)
number:     495
level:      Medium
lcurl:      teemo-attacking
youtube:    X403EVcAREI
bilibili1:  //player.bilibili.com/player.html?aid=884716530&bvid=BV1LK4y1Y75e&cid=239226213&page=1
xigua:      
date:       2020-09-26
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - 
---

### 题目

In LOL world, there is a hero called Teemo and his attacking can make his enemy Ashe be in poisoned condition. Now, given the Teemo's attacking ascending time series towards Ashe and the poisoning time duration per Teemo's attacking, you need to output the total time that Ashe is in poisoned condition.

You may assume that Teemo attacks at the very beginning of a specific time point, and makes Ashe be in poisoned condition immediately.

### 解题思路

总时间加，后一次攻击与前一次的时间差与duration的较小值

### 代码
```python
class Solution:
    def findPoisonedDuration(self, timeSeries: List[int], duration: int) -> int:
        l = len(timeSeries)
        if l == 0:
            return 0
        if l == 1:
            return duration
        res = duration
        for i in range(1, l):
            res += min(timeSeries[i] - timeSeries[i - 1], duration)
        return res
```
