---
layout:     post
title:      LeetCode 165 Compare Version Numbers (Python)
number:     165
level:      Medium
lcurl:      compare-version-numbers
youtube:    _mBhxiAo_P8
bilibili1:  //player.bilibili.com/player.html?aid=754619975&bvid=BV1Pk4y117dF&cid=233689867&page=1
xigua:      
date:       2020-09-09
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - String
---

### 题目

Compare two version numbers version1 and version2.
If version1 > version2 return 1; if version1 < version2 return -1;otherwise return 0.

You may assume that the version strings are non-empty and contain only digits and the . character.

The . character does not represent a decimal point and is used to separate number sequences.

For instance, 2.5 is not "two and a half" or "half way to version three", it is the fifth second-level revision of the second first-level revision.

You may assume the default revision number for each level of a version number to be 0. For example, version number 3.4 has a revision number of 3 and 4 for its first and second level revision number. Its third and fourth level revision number are both 0.

### 解题思路

想通过 . split，将两个版本的每一段，转成int进行比较，如果一个版本号长与另一个，则短的部分均为0

### 代码
```python
class Solution:
    def compareVersion(self, version1: str, version2: str) -> int:
        v1, v2 = version1.split('.'), version2.split('.')
        l1, l2 = len(v1), len(v2)
        for i in range(max(l1, l2)):
            p1 = int(v1[i]) if i < l1 else 0
            p2 = int(v2[i]) if i < l2 else 0
            if p1 > p2:
                return 1
            elif p1 < p2:
                return -1
        return 0
```
