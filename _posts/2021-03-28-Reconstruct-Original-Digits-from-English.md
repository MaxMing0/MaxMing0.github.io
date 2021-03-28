---
layout:     post
title:      LeetCode 423 Reconstruct Original Digits from English (Python)
number:     423
level:      Medium
lcurl:      reconstruct-original-digits-from-english
youtube:    7CB7Ggj5az8
bilibili1:  //player.bilibili.com/player.html?aid=844835149&bvid=BV1554y1h73S&cid=316651813&page=1
xigua:      
date:       2021-03-28
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - 
---

### 题目

Given a non-empty string containing an out-of-order English representation of digits 0-9, output the digits in ascending order.

Note:
1. Input contains only lowercase English letters.
1. Input is guaranteed to be valid and can be transformed to its original digits. That means invalid inputs such as "abc" or "zerone" are not permitted.
1. Input length is less than 50,000.

### 解题思路

将字符串存入计数器，找到每个单词的特殊字母求出个数

### 代码
```python
class Solution:
    def originalDigits(self, s: str) -> str:
        ct = Counter(s)
        res = [
            ct["z"],
            ct["o"] - ct["z"] - ct["w"] - ct["u"],
            ct["w"],
            ct["t"] - ct["w"] - ct["g"],
            ct["u"],
            ct["f"] - ct["u"],
            ct["x"],
            ct["s"] - ct["x"],
            ct["g"],
            ct["i"] - ct["x"] - ct["g"] - ct["f"] + ct["u"],
        ]
        return "".join(str(d) * c for d, c in enumerate(res))
```
