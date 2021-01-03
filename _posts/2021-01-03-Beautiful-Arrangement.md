---
layout:     post
title:      LeetCode 526 Beautiful Arrangement (Python)
number:     526
level:      Medium
lcurl:      beautiful-arrangement
youtube:    -M1G9RLcvuQ
bilibili1:  //player.bilibili.com/player.html?aid=501073110&bvid=BV1DK411M7QR&cid=276776784&page=1
xigua:      
date:       2020-01-03
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - DFS
---

### 题目

Suppose you have n integers from 1 to n. We define a beautiful arrangement as an array that is constructed by these n numbers successfully if one of the following is true for the ith position (1 <= i <= n) in this array:

- The number at the ith position is divisible by i.
- i is divisible by the number at the ith position.
Given an integer n, return the number of the beautiful arrangements that you can construct.

### 解题思路

递归求出所有可能的排列

### 代码
```python
class Solution:
    def countArrangement(self, n: int) -> int:
        def dfs(num, now):
            if now == 0:
                res[0] += 1
                return
            for i in range(now, 0, -1):
                num[i], num[now] = num[now], num[i]
                if num[now] % now == 0 or now % num[now] == 0:
                    dfs(num, now - 1)
                num[now], num[i] = num[i], num[now]

        res = [0]
        dfs([i for i in range(n + 1)], n)
        return res[0]
```
