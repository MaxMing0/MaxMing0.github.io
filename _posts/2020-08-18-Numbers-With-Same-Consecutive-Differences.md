---
layout:     post
title:      LeetCode 967 Numbers With Same Consecutive Differences (Python)
number:     967
level:      Medium
lcurl:      numbers-with-same-consecutive-differences
youtube:    ONZQSxLCdW0
bilibili1:  //player.bilibili.com/player.html?aid=456752089&bvid=BV12541187Nq&cid=225869153&page=1
xigua:      
date:       2020-08-18
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - BFS
---

### 题目

Return all non-negative integers of length N such that the absolute difference between every two consecutive digits is K.

Note that every number in the answer must not have leading zeros except for the number 0 itself. For example, 01 has one leading zero and is invalid, but 0 is valid.

You may return the answer in any order.

### 解题思路

BFS，先确定第一位为0-9，然后后面可以是个位数+K或者-K，但是要在0到9之间，如果K=0，要去重

### 代码
```python
class Solution:
    def numsSameConsecDiff(self, N: int, K: int) -> List[int]:
        if N == 1:
            return range(10)
        q = range(1, 10)
        for i in range(N - 1):
            tmp = []
            for n in q:
                for d in set([n % 10 + K, n % 10 - K]):
                    if 0 <= d < 10:
                        tmp.append(n * 10 + d)
            q = tmp
        return q
```
