---
layout:     post
title:      LeetCode 771 Jewels and Stones (Python)
number:     771
level:      Easy
lcurl:      jewels-and-stones
youtube:    vRwuT6oQ2o8
bilibili1:  //player.bilibili.com/player.html?aid=795594500&bvid=BV1RC4y1W7yH&cid=186042763&page=1
xigua:      
date:       2020-05-02
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Hash Set
---

### 题目

You're given strings J representing the types of stones that are jewels, and S representing the stones you have.  Each character in S is a type of stone you have.  You want to know how many of the stones you have are also jewels.

The letters in J are guaranteed distinct, and all characters in J and S are letters. Letters are case sensitive, so "a" is considered a different type of stone from "A".

### 解题思路

遍历S中的每一个字符，判断是否在J中出现，判断的时候吧J转换成Set

### 代码
```python
class Solution:
    def numJewelsInStones(self, J: str, S: str) -> int:
        res = 0
        for s in S:
            if s in set(J):
                res += 1
        return res
```
