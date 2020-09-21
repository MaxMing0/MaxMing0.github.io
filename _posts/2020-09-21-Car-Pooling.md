---
layout:     post
title:      LeetCode 1094 Car Pooling (Python)
number:     1094
level:      Medium
lcurl:      car-pooling
youtube:    Dp0cCSmzpBI
bilibili1:  
xigua:      
date:       2020-09-21
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - 
---

### 题目

You are driving a vehicle that has capacity empty seats initially available for passengers.  The vehicle only drives east (ie. it cannot turn around and drive west.)

Given a list of trips, trip[i] = [num_passengers, start_location, end_location] contains information about the i-th trip: the number of passengers that must be picked up, and the locations to pick them up and drop them off.  The locations are given as the number of kilometers due east from your vehicle's initial location.

Return true if and only if it is possible to pick up and drop off all passengers for all the given trips. 

### 解题思路

1. 对所有上车和下车的位置进行排序，按照顺序处理，如果在任何一个时刻不符合条件，就返回false
2. 用一个长度为1000的数组存每一个位置上下车的人数差，遍历这个数组，如果在任何一个时刻不符合条件，就返回false

### 代码
```python
class Solution:
    def carPooling(self, trips: List[List[int]], capacity: int) -> bool:
        pick, drop = [], []
        for t in trips:
            pick.append((t[1], t[0]))
            drop.append((t[2], t[0]))
        pick.sort()
        drop.sort()
        p = d = cur = 0        
        while p < len(trips) and d < len(trips):
            pick_pos, pick_num = pick[p]
            drop_pos, drop_num = drop[d]
            if pick_pos < drop_pos:
                cur += pick_num
                if cur > capacity:
                    return False
                p += 1
            else:
                cur -= drop_num
                d += 1
        return True
```

```python
class Solution:
    def carPooling(self, trips: List[List[int]], capacity: int) -> bool:
        pos = [0] * 1001
        for trip in trips:
            pos[trip[1]] += trip[0]
            pos[trip[2]] -= trip[0]
        cur = 0
        for diff in pos:
            cur += diff
            if cur > capacity:
                return False
        return True
```
