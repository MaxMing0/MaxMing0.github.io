---
layout:     post
title:      LeetCode 2336 Smallest Number in Infinite Set (Python)
number:     2336
level:      Medium
lcurl:      smallest-number-in-infinite-set
youtube:    h4a3N5qsXmo
bilibili1:  
xigua:      
date:       2022-4-24
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Design
---

### 题目

You have a set which contains all positive integers [1, 2, 3, 4, 5, ...].

Implement the SmallestInfiniteSet class:

- SmallestInfiniteSet() Initializes the SmallestInfiniteSet object to contain all positive integers.
- int popSmallest() Removes and returns the smallest integer contained in the infinite set.
- void addBack(int num) Adds a positive integer num back into the infinite set, if it is not already in the infinite set.

### 解题思路

维护一个堆，存加入符合条件的数，并在一个set中存入同样的数，用来判断是否已经存在，如果堆里有元素，就pop堆里最小的

### 代码
```python
class SmallestInfiniteSet:

    def __init__(self):
        self.cur = 1
        self.addlist = []
        self.addset = set()

    def popSmallest(self) -> int:
        if self.addlist:
            ret = heapq.heappop(self.addlist)
            self.addset.discard(ret)
        else:
            ret = self.cur
            self.cur += 1
        return ret

    def addBack(self, num: int) -> None:
        if num >= self.cur or num in self.addset:
            return
        heapq.heappush(self.addlist, num)
        self.addset.add(num)
```
