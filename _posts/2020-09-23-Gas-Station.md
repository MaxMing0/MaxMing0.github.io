---
layout:     post
title:      LeetCode 134 Gas Station (Python)
number:     134
level:      Medium
lcurl:      gas-station
youtube:    PY0GUlRFTxg
bilibili1:  //player.bilibili.com/player.html?aid=839716225&bvid=BV1754y1176F&cid=238227261&page=1
xigua:      
date:       2020-09-23
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Greedy
---

### 题目

There are N gas stations along a circular route, where the amount of gas at station i is gas[i].

You have a car with an unlimited gas tank and it costs cost[i] of gas to travel from station i to its next station (i+1). You begin the journey with an empty tank at one of the gas stations.

Return the starting gas station's index if you can travel around the circuit once in the clockwise direction, otherwise return -1.

Note:

- If there exists a solution, it is guaranteed to be unique.
- Both input arrays are non-empty and have the same length.
- Each element in the input arrays is a non-negative integer.

### 解题思路

贪心，从0号加油站开始，一旦无法到达某个加油站，就从下一个作为起点，知道遍历完所有的加油站，如果总的可加的油大于总的所需要的油，则存在一个加油站可行，就是算法记录的加油站，证明使用反证法

### 代码
```python
class Solution:
    def canCompleteCircuit(self, gas: List[int], cost: List[int]) -> int:
        l = len(gas)
        start = cur = tot = 0
        for i in range(l):
            t = gas[i] - cost[i]
            tot += t
            cur += t
            if cur < 0:
                cur, start = 0, i + 1
        return -1 if tot < 0 else start
```
