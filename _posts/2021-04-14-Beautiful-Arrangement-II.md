---
layout:     post
title:      LeetCode 667 Beautiful Arrangement II (Python)
number:     667
level:      Medium
lcurl:      beautiful-arrangement-ii
youtube:    lYXnvahuug0
bilibili1:  //player.bilibili.com/player.html?aid=845012401&bvid=BV1j54y1b7Br&cid=324317267&page=1
xigua:      
date:       2021-04-14
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - 
---

### 题目

Given two integers n and k, construct a list answer that contains n different positive integers ranging from 1 to n and obeys the following requirement:

Suppose this list is answer = [a1, a2, a3, ... , an], then the list [|a1 - a2|, |a2 - a3|, |a3 - a4|, ... , |an-1 - an|] has exactly k distinct integers.
Return the list answer. If there multiple valid answers, return any of them.

### 解题思路

直接进行构造，先把1到n-k放到结果里，之后每个数相差从k到1

### 代码
```python
class Solution:
    def constructArray(self, n: int, k: int) -> List[int]:
        res = list(range(1, n - k + 1))
        f, d = 1, k
        for i in range(k):
            res.append(res[-1] + f * d)
            f = -f
            d -= 1
        return res
```
