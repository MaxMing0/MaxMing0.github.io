---
layout:     post
title:      LeetCode 933 Number of Recent Calls (Python)
number:     933
level:      Easy
lcurl:      number-of-recent-calls
youtube:    UqSHAksYYPI
bilibili1:  //player.bilibili.com/player.html?aid=329779413&bvid=BV1gA41177jm&cid=240866554&page=1
xigua:      
date:       2020-10-01
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Design
---

### 题目

You have a RecentCounter class which counts the number of recent requests within a certain time frame.

Implement the RecentCounter class:

- RecentCounter() Initializes the counter with zero recent requests.
- int ping(int t) Adds a new request at time t, where t represents some time in milliseconds, and returns the number of requests that has happened in the past 3000 milliseconds (including the new request). Specifically, return the number of requests that have happened in the inclusive range [t - 3000, t].
It is guaranteed that every call to ping uses a strictly larger value of t than the previous call.

### 解题思路

维护一个双向队列，每次将新的时间加到队尾，从左边开始遍历，把所有不在范围内的时间删除，返回队列的大小

### 代码
```python
class RecentCounter:

    def __init__(self):
         self.q = collections.deque()

    def ping(self, t: int) -> int:
        self.q.append(t)
        while self.q[0] < t - 3000:
            self.q.popleft()
        return len(self.q)
```
