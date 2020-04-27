---
layout:     post
title:      LeetCode 1046 Last Stone Weight (Python)
number:     1046
level:      Easy
lcurl:      last-stone-weight
youtube:    dWaZt40InAA
bilibili1:  //player.bilibili.com/player.html?aid=840172793&bvid=BV1w54y197Ln&cid=177352739&page=1
xigua:      
date:       2020-04-26
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Greedy
    - Heap
---

### 题目

We have a collection of stones, each stone has a positive integer weight.

Each turn, we choose the two heaviest stones and smash them together.  Suppose the stones have weights x and y with x <= y.  The result of this smash is:
- If x == y, both stones are totally destroyed;
- If x != y, the stone of weight x is totally destroyed, and the stone of weight y has new weight y-x.

At the end, there is at most 1 stone left.  Return the weight of this stone (or 0 if there are no stones left.)

### 解题思路



### 代码
```python
import heapq
class Solution:
    def lastStoneWeight(self, stones: List[int]) -> int:
        stones = [-s for s in stones]
        heapq.heapify(stones)
        while len(stones) >= 2:
            s1 = heapq.heappop(stones)
            s2 = heapq.heappop(stones)
            if s1 != s2:
                heapq.heappush(stones, s1 - s2)
        return -stones[0] if stones else 0
```