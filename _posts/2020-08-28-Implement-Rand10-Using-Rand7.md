---
layout:     post
title:      LeetCode 470 Implement Rand10() Using Rand7() (Python)
number:     470
level:      Medium
lcurl:      implement-rand10-using-rand7
youtube:    93DWLAJCEzU
bilibili1:  //player.bilibili.com/player.html?aid=711878055&bvid=BV1AD4y1m7Qb&cid=229825732&page=1
xigua:      
date:       2020-08-28
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Random
---

### 题目

Given a function rand7 which generates a uniform random integer in the range 1 to 7, write a function rand10 which generates a uniform random integer in the range 1 to 10.

Do NOT use system's Math.random().

### 解题思路

随机两次，通过这个两个数可以生产1-49直接的随机数，如果在1-40内，`%10+1`为结果，如果不在，继续随机

### 代码
```python
class Solution:
    def rand10(self):
        """
        :rtype: int
        """
        while True:
            r1, r2 = rand7(), rand7()
            t = r1 + (r2 - 1) * 7
            if t <= 40:
                return t % 10 + 1
```
