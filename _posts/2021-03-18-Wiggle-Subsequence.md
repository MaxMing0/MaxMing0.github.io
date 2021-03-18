---
layout:     post
title:      LeetCode 376 Wiggle Subsequence (Python)
number:     376
level:      Medium
lcurl:      wiggle-subsequence
youtube:    inPQObejpyU
bilibili1:  //player.bilibili.com/player.html?aid=714697240&bvid=BV16X4y1376k&cid=312168080&page=1
xigua:      
date:       2021-03-18
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Greedy
---

### 题目

class Solution:
    def wiggleMaxLength(self, nums: List[int]) -> int:
        n = len(nums)
        if n < 2:
            return n
        pre = nums[1] - nums[0]
        res = 1 if pre == 0 else 2
        for i in range(2, n):
            dif = nums[i] - nums[i - 1]
            if (dif > 0 and pre <= 0) or (dif < 0 and pre >= 0):
                res += 1
                pre = dif
        return res

### 解题思路

贪心，如果能构成交替的序列就加上这个数，如果后面的数更小（或者更打）就替换之前的数（写的时候并不需要替换，只需要记录正负号）

### 代码
```python
class Solution:
    def wiggleMaxLength(self, nums: List[int]) -> int:
        n = len(nums)
        if n < 2:
            return n
        pre = nums[1] - nums[0]
        res = 1 if pre == 0 else 2
        for i in range(2, n):
            dif = nums[i] - nums[i - 1]
            if (dif > 0 and pre <= 0) or (dif < 0 and pre >= 0):
                res += 1
                pre = dif
        return res
```
