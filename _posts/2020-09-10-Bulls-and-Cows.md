---
layout:     post
title:      LeetCode 299 Bulls and Cows (Python)
number:     299
level:      Easy
lcurl:      bulls-and-cows
youtube:    yWpoSI_oHX0
bilibili1:  //player.bilibili.com/player.html?aid=202036065&bvid=BV1bh411R7n4&cid=233995357&page=1
xigua:      
date:       2020-09-10
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Hash Table
---

### 题目

You are playing the following Bulls and Cows game with your friend: You write down a number and ask your friend to guess what the number is. Each time your friend makes a guess, you provide a hint that indicates how many digits in said guess match your secret number exactly in both digit and position (called "bulls") and how many digits match the secret number but locate in the wrong position (called "cows"). Your friend will use successive guesses and hints to eventually derive the secret number.

Write a function to return a hint according to the secret number and friend's guess, use A to indicate the bulls and B to indicate the cows. 

Please note that both secret number and friend's guess may contain duplicate digits.

### 解题思路

比较对应位置的数字，如果相同，A的个数加一，不同就分别放到两个计数器中，最后如果某个数字在两个计数器中均出现，则取较小次数，加到B中

### 代码
```python
class Solution:
    def getHint(self, secret: str, guess: str) -> str:
        s1, s2 = defaultdict(int), defaultdict(int)
        A = B = 0
        for s, g in zip(secret, guess):
            if s == g:
                A += 1
            else:
                s1[s] += 1
                s2[g] += 1
        for k in s1.keys():
            if k in s2:
                B += min(s1[k], s2[k])
        return "%sA%sB" % (A, B)
```
