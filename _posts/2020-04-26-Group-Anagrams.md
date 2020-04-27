---
layout:     post
title:      LeetCode 49 Group Anagrams (Python)
number:     49
level:      Medium
lcurl:      group-anagrams
youtube:    Ge04OM0r0d8
bilibili1:  //player.bilibili.com/player.html?aid=455231591&bvid=BV1n5411t79G&cid=174689817&page=1
xigua:      
date:       2020-04-26
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Hash Table
---

### 题目

Given an array of strings, group anagrams together.

### 解题思路



### 代码
```python
from collections import defaultdict
class Solution:
    def groupAnagrams(self, strs: List[str]) -> List[List[str]]:
        dic = defaultdict(list)
        for s in strs:
            dic[''.join(sorted(s))].append(s)
        return dic.values()
```