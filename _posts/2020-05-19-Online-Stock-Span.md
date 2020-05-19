---
layout:     post
title:      LeetCode 901 Online Stock Span (Python)
number:     901
level:      Medium
lcurl:      online-stock-span
youtube:    ZTelsIrE11w
bilibili1:  //player.bilibili.com/player.html?aid=838173110&bvid=BV1Jg4y1B74H&cid=192820207&page=1
xigua:      
date:       2020-05-19
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Stack
---

### 题目

Write a class StockSpanner which collects daily price quotes for some stock, and returns the span of that stock's price for the current day.

The span of the stock's price today is defined as the maximum number of consecutive days (starting from today and going backwards) for which the price of the stock was less than or equal to today's price.

For example, if the price of a stock over the next 7 days were [100, 80, 60, 70, 60, 75, 85], then the stock spans would be [1, 1, 1, 2, 1, 4, 6].

### 解题思路

维护一个严格递降的栈，在入栈的时候，也把当前的span加进去，这样在pop的时候，就把被pop的span加到新的数中

### 代码
```python
class StockSpanner:

    def __init__(self):
        self.stack = [(0, float('inf'))]
        
    def next(self, price: int) -> int:
        res = 1
        while price >= self.stack[-1][1]:
            res += self.stack.pop()[0]
        self.stack.append((res, price))
        return res
```
