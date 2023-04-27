---
layout:     post
title:      LeetCode 319 Bulb Switcher (Python)
number:     319
level:      Medium
lcurl:      bulb-switcher
youtube:    sJ7Qf2rXRuc
bilibili1:  
xigua:      
date:       2023-04-26
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Math
---

### 题目

There are n bulbs that are initially off. You first turn on all the bulbs, then you turn off every second bulb.

On the third round, you toggle every third bulb (turning on if it's off or turning off if it's on). For the ith round, you toggle every i bulb. For the nth round, you only toggle the last bulb.

Return the number of bulbs that are on after n rounds.

### 解题思路

只有处在完全平方数位置的灯泡会亮

### 代码
```python
class Solution:
    def bulbSwitch(self, n: int) -> int:
        return int(sqrt(n))
```
