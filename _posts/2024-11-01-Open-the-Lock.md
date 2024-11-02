---
layout:     post
title:      LeetCode 752 Open the Lock (Python)
number:     752
level:      Medium
lcurl:      open-the-lock
youtube:    
bilibili1:  
xigua:      
date:       2024-11-01
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - 
---

### 题目

You have a lock in front of you with 4 circular wheels. Each wheel has 10 slots: '0', '1', '2', '3', '4', '5', '6', '7', '8', '9'. The wheels can rotate freely and wrap around: for example we can turn '9' to be '0', or '0' to be '9'. Each move consists of turning one wheel one slot.

The lock initially starts at '0000', a string representing the state of the 4 wheels.

You are given a list of deadends dead ends, meaning if the lock displays any of these codes, the wheels of the lock will stop turning and you will be unable to open it.

Given a target representing the value of the wheels that will unlock the lock, return the minimum total number of turns required to open the lock, or -1 if it is impossible.

### 解题思路

BFS，如果遇到了deadend的状态，就跳过，否则可以对每一个位置加1或者减1

### 代码
```python
class Solution:
    def openLock(self, deadends: List[str], target: str) -> int:
        dead = set(deadends)
        q = deque([('0000', 0)])
        visited = {'0000'}
        while q:
            cur, step = q.popleft()
            if cur == target:
                return step
            if cur in dead:
                continue
            for i in range(4):
                for d in [1, -1]:
                    nei = (int(cur[i]) + d) % 10
                    tmp = cur[:i] + str(nei) + cur[i + 1:]
                    if tmp not in visited:
                        visited.add(tmp)
                        q.append((tmp, step + 1))
        return -1
```
