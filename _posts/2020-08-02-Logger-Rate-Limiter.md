---
layout:     post
title:      LeetCode 359 Logger Rate Limiter (Python)
number:     359
level:      Easy
lcurl:      logger-rate-limiter
youtube:    MVAVeZRTZgU
bilibili1:  //player.bilibili.com/player.html?aid=584067897&bvid=BV1k64y1F7dE&cid=219381209&page=1
xigua:      
date:       2020-08-01
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Hash Table
    - Design
---

### 题目

Design a logger system that receive stream of messages along with its timestamps, each message should be printed if and only if it is not printed in the last 10 seconds.

Given a message and a timestamp (in seconds granularity), return true if the message should be printed in the given timestamp, otherwise returns false.

It is possible that several messages arrive roughly at the same time.

### 解题思路

使用字典存每个log上次输出的时间，如果超过10s就输出并更新时间

### 代码
```python
class Logger:

    def __init__(self):
        """
        Initialize your data structure here.
        """
        self.dic = {}

    def shouldPrintMessage(self, timestamp: int, message: str) -> bool:
        """
        Returns true if the message should be printed in the given timestamp, otherwise returns false.
        If this method returns false, the message will not be printed.
        The timestamp is in seconds granularity.
        """
        if message not in self.dic or self.dic[message] + 10 <= timestamp:
            self.dic[message] = timestamp
            return True
        return False
```
