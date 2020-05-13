---
layout:     post
title:      LeetCode 402 Remove K Digits (Python)
number:     402
level:      Medium
lcurl:      remove-k-digits
youtube:    dDJX1ZL8ZOw
bilibili1:  player.bilibili.com/player.html?aid=413229360&bvid=BV1PV411C79X&cid=190529786&page=1
xigua:      
date:       2020-05-13
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Greedy
    - Stack
---

### 题目

Given a non-negative integer num represented as a string, remove k digits from the number so that the new number is the smallest possible.

Note:
- The length of num is less than 10002 and will be ≥ k.
- The given num does not contain any leading zero.

### 解题思路

贪心，尽量使得这个数是不降的，使用一个栈来维护，如果已经是不降的了，那么就从最后开始删

### 代码
```python
class Solution:
    def removeKdigits(self, num: str, k: int) -> str:
        if k == len(num):
            return '0'
        stack = []
        for n in num:
            while k and stack and n < stack[-1]:
                stack.pop()
                k -= 1
            stack.append(n)
        for i in range(k):
            stack.pop()
        return ''.join(stack).lstrip('0') or '0'
```
