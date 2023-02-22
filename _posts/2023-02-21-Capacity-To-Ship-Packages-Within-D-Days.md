---
layout:     post
title:      LeetCode 1011 Capacity To Ship Packages Within D Days (Python)
number:     1011
level:      Medium
lcurl:      capacity-to-ship-packages-within-d-days
youtube:    uViLdjej4q8
bilibili1:  
xigua:      
date:       2023-02-21
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Binary Search
---

### 题目

A conveyor belt has packages that must be shipped from one port to another within days days.

The ith package on the conveyor belt has a weight of weights[i]. Each day, we load the ship with packages on the conveyor belt (in the order given by weights). We may not load more weight than the maximum weight capacity of the ship.

Return the least weight capacity of the ship that will result in all the packages on the conveyor belt being shipped within days days.

### 解题思路

二分答案，枚举船的最大容积，判断是否可以在`days`天内运完所有的包裹

### 代码
```python
class Solution:
    def shipWithinDays(self, weights: List[int], days: int) -> int:
        def check(cap):
            day_need, cur_load = 1, 0
            for weight in weights:
                cur_load += weight
                if cur_load > cap:
                    cur_load = weight
                    day_need += 1
                    if day_need > days:
                        return False
            return True

        l, r = max(weights), sum(weights)
        while l < r:
            m = (l + r) // 2
            if check(m):
                r = m
            else:
                l = m + 1
        return l
```
