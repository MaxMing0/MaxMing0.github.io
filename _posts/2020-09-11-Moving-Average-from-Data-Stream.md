---
layout:     post
title:      LeetCode 346 Moving Average from Data Stream (Python)
number:     346
level:      Easy
lcurl:      moving-average-from-data-stream
youtube:    Mg11BehSrpk
bilibili1:  //player.bilibili.com/player.html?aid=414608848&bvid=BV1xV411m73u&cid=234493275&page=1
xigua:      
date:       2020-09-05
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Design
---

### 题目

Given a stream of integers and a window size, calculate the moving average of all integers in the sliding window.

### 解题思路

维护一个deque，当数字超过size之后，每次弹出最左边的数，求和减去这个数，加上新的数

### 代码
```python
class MovingAverage:

    def __init__(self, size: int):
        """
        Initialize your data structure here.
        """
        self.size = size
        self.q = deque()
        self.count = 0
        self.sum = 0

    def next(self, val: int) -> float:
        self.count += 1
        self.q.append(val)
        tail = self.q.popleft() if self.count > self.size else 0
        self.sum = self.sum - tail + val
        return self.sum / min(self.size, self.count)
```
