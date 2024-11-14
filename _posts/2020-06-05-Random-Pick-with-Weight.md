---
layout:     post
title:      LeetCode 528 Random Pick with Weight (Python)
number:     528
level:      Medium
lcurl:      random-pick-with-weight
youtube:    TPTlVWi1p_M
bilibili1:  //player.bilibili.com/player.html?aid=413476953&bvid=BV1UV411r7MK&cid=198873603&page=1
xigua:      
date:       2020-06-05
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Binary Search
    - Random
---

### 题目

Given an array w of positive integers, where w[i] describes the weight of index i, write a function pickIndex which randomly picks an index in proportion to its weight.

Note:

1. 1 <= w.length <= 10000
2. 1 <= w[i] <= 10^5
3. pickIndex will be called at most 10000 times.

### 解题思路

求石头重量的部分和，随机0到总和之间的一个随机数，二分搜索这个随机数的位置

### 代码
```python
import random
import bisect
class Solution:

    def __init__(self, w: List[int]):
        self.sum = [w[0]]
        for n in w[1:]:
            self.sum.append(self.sum[-1] + n)

    def pickIndex(self) -> int:
        return bisect.bisect(self.sum, self.sum[-1] * random.random())

    def pickIndex(self) -> int:
        def search(n):
            l, r = 0, len(self.sum)    
            while l < r:
                m = (l + r) // 2
                if self.sum[m] <= n:
                    l = m + 1
                else:
                    r = m
            return l
        num = random.randint(0, self.sum[-1] - 1)
        return search(num)

# Your Solution object will be instantiated and called as such:
# obj = Solution(w)
# param_1 = obj.pickIndex()
```
