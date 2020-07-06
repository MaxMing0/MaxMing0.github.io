---
layout:     post
title:      LeetCode 1503 Last Moment Before All Ants Fall Out of a Plank (Python)
number:     1503
level:      Medium
lcurl:      last-moment-before-all-ants-fall-out-of-a-plank
youtube:    jgFG_JDbyoI
bilibili1:  //player.bilibili.com/player.html?aid=838767300&bvid=BV1Fg4y1i7na&cid=209422826&page=1
xigua:      
date:       2020-07-05
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - 
---

### 题目

We have a wooden plank of the length n units. Some ants are walking on the plank, each ant moves with speed 1 unit per second. Some of the ants move to the left, the other move to the right.

When two ants moving in two different directions meet at some point, they change their directions and continue moving again. Assume changing directions doesn't take any additional time.

When an ant reaches one end of the plank at a time t, it falls out of the plank imediately.

Given an integer n and two integer arrays left and right, the positions of the ants moving to the left and the right. Return the moment when the last ant(s) fall out of the plank.



### 解题思路

我们可以假设在两只蚂蚁相遇之后，不会转头，而是各自继续向前，效果是相同的

### 代码
```python
class Solution:
    def getLastMoment(self, n: int, left: List[int], right: List[int]) -> int:
        return max(max(left or [0]), n - min(right or [n]))
```
