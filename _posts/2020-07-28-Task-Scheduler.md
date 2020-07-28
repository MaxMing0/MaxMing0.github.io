---
layout:     post
title:      LeetCode 621 Task Scheduler (Python)
number:     621
level:      Medium
lcurl:      task-scheduler
youtube:    7RDorlt6H7A
bilibili1:  //player.bilibili.com/player.html?aid=371593587&bvid=BV1LZ4y1M7Bg&cid=217585819&page=1
xigua:      
date:       2020-07-28
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Greedy
---

### 题目

You are given a char array representing tasks CPU need to do. It contains capital letters A to Z where each letter represents a different task. Tasks could be done without the original order of the array. Each task is done in one unit of time. For each unit of time, the CPU could complete either one task or just be idle.

However, there is a non-negative integer n that represents the cooldown period between two same tasks (the same letter in the array), that is that there must be at least n units of time between any two same tasks.

You need to return the least number of units of times that the CPU will take to finish all the given tasks.

### 解题思路

贪心，尽量先安排出现次数最多的任务，假设k次，要间隔n个时间，所以可以分成k-1组，每组n+1个时间，这样就可以得到最少需要的时间了，和任务的总数比，取较大的结果

### 代码
```python
class Solution:
    def leastInterval(self, tasks: List[str], n: int) -> int:
        ct = Counter(tasks)
        maxx = max(ct.values())
        nmax = len([v for v in ct.values() if v == maxx])
        return max(len(tasks), (maxx - 1) * (n + 1) + nmax)
```
