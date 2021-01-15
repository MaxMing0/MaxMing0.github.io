---
layout:     post
title:      LeetCode 1646 Get Maximum in Generated Array (Python)
number:     1646
level:      Easy
lcurl:      get-maximum-in-generated-array
youtube:    yAJdHMUJd24
bilibili1:  //player.bilibili.com/player.html?aid=843729513&bvid=BV1W54y1s7mg&cid=282970968&page=1
xigua:      
date:       2021-01-15
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - 
---

### 题目

You are given an integer n. An array nums of length n + 1 is generated in the following way:

- nums[0] = 0
- nums[1] = 1
- nums[2 * i] = nums[i] when 2 <= 2 * i <= n
- nums[2 * i + 1] = nums[i] + nums[i + 1] when 2 <= 2 * i + 1 <= n
Return the maximum integer in the array nums​​​.

### 解题思路

根据题目要求模拟生成这个数组，求最大值

### 代码
```python
class Solution:
    def getMaximumGenerated(self, n: int) -> int:
        if n == 0:
            return 0
        nums = [0] * (n + 1)
        nums[1] = 1
        for i in range(2, n + 1):
            if i % 2:
                nums[i] = nums[i // 2] + nums[i // 2 + 1]
            else:
                nums[i] = nums[i // 2]
        return max(nums)
```
