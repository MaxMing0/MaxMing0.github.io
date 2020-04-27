---
layout:     post
title:      LeetCode 136 Single Number (Python)
number:     136
level:      Easy
lcurl:      single-number/
youtube:    igjaxBhw5mQ
bilibili1:  //player.bilibili.com/player.html?aid=667561277&bvid=BV1pa4y1t7tr&cid=173257676&page=1
xigua:      
date:       2020-04-26
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Bit Manipulation
---

### 题目

Given a non-empty array of integers, every element appears twice except for one. Find that single one.

Note:

Your algorithm should have a linear runtime complexity. Could you implement it without using extra memory?

### 解题思路
对于异或运算，我们知道 a^a=0; a^0=a，所以我们就把所有的数都异或到一起，那么所有出现两次的数就会是0，只留下最后一个只出现过一次的数字了。


### 代码
```python
import functools
class Solution:
    def singleNumber(self, nums: List[int]) -> int:
        return functools.reduce(lambda x, y: x ^ y, nums)
```