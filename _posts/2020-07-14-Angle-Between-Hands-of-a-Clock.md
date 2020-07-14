---
layout:     post
title:      LeetCode 1344 Angle Between Hands of a Clock (Python)
number:     1344
level:      Medium
lcurl:      angle-between-hands-of-a-clock
youtube:    uX5erOCjekk
bilibili1:  //player.bilibili.com/player.html?aid=286288495&bvid=BV1Zf4y197Uh&cid=212355627&page=1
xigua:      
date:       2020-07-14
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Math
---

### 题目

Given two numbers, hour and minutes. Return the smaller angle (in degrees) formed between the hour and the minute hand.

### 解题思路

时针和分针的夹角是`5.5 * (hour * 60 + minutes) % 360`，然后取小于等于180度的角

### 代码
```python
class Solution:
    def angleClock(self, hour: int, minutes: int) -> float:
        angle = 5.5 * (hour * 60 + minutes) % 360
        return angle if angle <= 180 else 360 - angle
```
