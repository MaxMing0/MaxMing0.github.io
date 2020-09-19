---
layout:     post
title:      LeetCode 1291 Sequential Digits (Python)
number:     1291
level:      Medium
lcurl:      sequential-digits
youtube:    7lb0eg3dG2w
bilibili1:  //player.bilibili.com/player.html?aid=244656988&bvid=BV11v411C7so&cid=236837023&page=1
xigua:      
date:       2020-09-19
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - 
---

### 题目

An integer has sequential digits if and only if each digit in the number is one more than the previous digit.

Return a sorted list of all the integers in the range [low, high] inclusive that have sequential digits.

### 解题思路

如果一个数符合条件，一定是“123456789”的一个连续子串，先枚举这个数的位数，再枚举长度，如果当前的数大于high，就可以停止了

### 代码
```python
class Solution:
    def sequentialDigits(self, low: int, high: int) -> List[int]:
        seq = '123456789'
        res = []
        for l in range(1, 10):
            for i in range(len(seq) - l + 1):
                num = int(seq[i: i + l])
                if num > high:
                    return res
                if num >= low:
                    res.append(num)
        return res
```
