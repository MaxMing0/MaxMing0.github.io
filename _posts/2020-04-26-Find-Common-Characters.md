---
layout:     post
title:      LeetCode 1002 Find Common Characters (Python)
number:     1002
level:      Easy
lcurl:      find-common-characters
youtube:    LDr3_aYeqF4
bilibili1:  //player.bilibili.com/player.html?aid=497809410&bvid=BV17K411j7XT&cid=180799223&page=1
xigua:      
date:       2020-04-26
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Hash Table
---

### 题目

Given an array A of strings made only from lowercase letters, return a list of all characters that show up in all strings within the list (including duplicates).  For example, if a character occurs 3 times in all strings but not 4 times, you need to include that character three times in the final answer.

You may return the answer in any order.

### 解题思路



### 代码
```python
class Solution:
    def commonChars(self, A: List[str]) -> List[str]:
        ct = Counter(A[0])
        for w in A[1:]:
            tmp = Counter(w)
            for key in list(ct.keys()):
                if key not in tmp:
                    del ct[key]
                else:
                    ct[key] = min(ct[key], tmp[key])
        res = []
        for key in ct:
            res += [key] * ct[key]
        return res
```