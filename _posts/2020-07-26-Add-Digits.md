---
layout:     post
title:      LeetCode 258 Add Digits (Python)
number:     258
level:      Easy
lcurl:      add-digits
youtube:    Z8V4329JX9A
bilibili1:  //player.bilibili.com/player.html?aid=841450402&bvid=BV1N54y1B7XU&cid=216830988&page=1
xigua:      
date:       2020-07-26
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Math
---

### 题目

Given a non-negative integer num, repeatedly add all its digits until the result has only one digit.

### 解题思路

可以通过找规律或者数学证明来得到O(1)的方法，基本过程请看视频

### 代码
```python
class Solution:
    def addDigits(self, num: int) -> int:
        if num <= 9:
            return num
        tmp = 0
        while num > 0:
            tmp += num % 10
            num //= 10
        return self.addDigits(tmp)
```
```python
class Solution:
    def addDigits(self, num: int) -> int:
        return (num - 1) % 9 + 1 if num else 0
```
