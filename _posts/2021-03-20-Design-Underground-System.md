---
layout:     post
title:      LeetCode 1396 Design Underground System (Python)
number:     1396
level:      Medium
lcurl:      design-underground-system
youtube:    V-XRuHFhuj0
bilibili1:  //player.bilibili.com/player.html?aid=332189008&bvid=BV1uA411N7q6&cid=312826743&page=1
xigua:      
date:       2021-03-20
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Design
---

### 题目

Implement the UndergroundSystem class:

- void checkIn(int id, string stationName, int t)
  - A customer with a card id equal to id, gets in the station stationName at time t.
  - A customer can only be checked into one place at a time.
- void checkOut(int id, string stationName, int t)
  - A customer with a card id equal to id, gets out from the station stationName at time t.
- double getAverageTime(string startStation, string endStation)
  - Returns the average time to travel between the startStation and the endStation.
The average time is computed from all the previous traveling from startStation to endStation that happened directly.
Call to getAverageTime is always valid.
You can assume all calls to checkIn and checkOut methods are consistent. If a customer gets in at time t1 at some station, they get out at time t2 with t2 > t1. All events happen in chronological order.

### 解题思路

使用两个字典，一个字典存user信息，进站的地点和时间，另一个字典存通过两个站之间所有user的通行时间，查询的时候求这些时间的平均值

### 代码
```python
class UndergroundSystem:

    def __init__(self):
        self.user = {}
        self.station = defaultdict(list)

    def checkIn(self, id: int, stationName: str, t: int) -> None:
        self.user[id] = (stationName, t)

    def checkOut(self, id: int, stationName: str, t: int) -> None:
        startStation, startTime = self.user[id]
        self.station[(startStation, stationName)].append(t - startTime)

    def getAverageTime(self, startStation: str, endStation: str) -> float:
        tmp = self.station[(startStation, endStation)]
        return sum(tmp) / len(tmp)
```
