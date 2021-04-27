---
layout:     post
title:      LeetCode 1642 Furthest Building You Can Reach (Python)
number:     1642
level:      Medium
lcurl:      furthest-building-you-can-reach
youtube:    MrxhfCBCGNU
bilibili1:  //player.bilibili.com/player.html?aid=375260117&bvid=BV1gZ4y1F7Zp&cid=329773442&page=1
xigua:      
date:       2021-04-26
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Greedy
---

### 题目

You are given an integer array heights representing the heights of buildings, some bricks, and some ladders.

You start your journey from building 0 and move to the next building by possibly using bricks or ladders.

While moving from building i to building i+1 (0-indexed),

- If the current building's height is greater than or equal to the next building's height, you do not need a ladder or bricks.
- If the current building's height is less than the next building's height, you can either use one ladder or (h[i+1] - h[i]) bricks.
Return the furthest building index (0-indexed) you can reach if you use the given ladders and bricks optimally.

### 解题思路

贪心，使用优先队列存所有需要使用梯子或者砖头的差值，先默认使用梯子，当梯子不够的时候，取最小的差值用砖头

### 代码
```python
class Solution:
    def furthestBuilding(self, heights: List[int], bricks: int, ladders: int) -> int:
        n = len(heights)
        q = []
        for i in range(1, n):
            dif = heights[i] - heights[i - 1]
            if dif > 0:
                heapq.heappush(q, dif)
                if len(q) > ladders:
                    bricks -= heapq.heappop(q)
                if bricks < 0:
                    return i - 1
        return n - 1
```
