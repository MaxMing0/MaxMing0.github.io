---
layout:     post
title:      LeetCode 264 Ugly Number II (Python)
number:     264
level:      Medium
lcurl:      ugly-number-ii
youtube:    FxV61rc2X3I
bilibili1:  //player.bilibili.com/player.html?aid=926200238&bvid=BV1vT4y1775u&cid=208960673&page=1
xigua:      
date:       2020-07-04
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - DP
    - Heap
---

### 题目

Write a program to find the n-th ugly number.

Ugly numbers are positive numbers whose prime factors only include 2, 3, 5.

### 解题思路

1. 使用优先队列，每次弹出最小的数，然后把这个数*2 *3 *5 加到队列中
2. 三个指针p2 p3 p5，分别指向下一个ugly可能由当前的数 *2 *3 *5 构成，找到这个最小的数，并把对应的指针+1

### 代码
```python
import heapq
class Solution:
    def __init__(self):
        self.num = []
        s = {1, }
        q = []
        heapq.heappush(q, 1)

        for i in range(1690):
            cur = heapq.heappop(q)
            self.num.append(cur)
            for j in [2, 3, 5]:
                tmp = cur * j
                if tmp not in s:
                    s.add(tmp)
                    heapq.heappush(q, tmp)
                    
    def nthUglyNumber(self, n: int) -> int:
        return self.num[n - 1]
```
```python
class Solution:
    def __init__(self):
        num = [1]
        p2 = p3 = p5 = 0
        for i in range(1690):
            tmp = min(num[p2] * 2, num[p3] * 3, num[p5] * 5)
            num.append(tmp)

            if tmp == num[p2] * 2: 
                p2 += 1
            if tmp == num[p3] * 3:
                p3 += 1
            if tmp == num[p5] * 5:
                p5 += 1
        self.num = num

    def nthUglyNumber(self, n: int) -> int:
        return self.num[n - 1]
```
