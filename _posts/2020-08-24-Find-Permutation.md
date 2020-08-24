---
layout:     post
title:      LeetCode 484 Find Permutation (Python)
number:     484
level:      Medium
lcurl:      find-permutation
youtube:    _dqRpS5CclQ
bilibili1:  
xigua:      //player.bilibili.com/player.html?aid=926801166&bvid=BV1NT4y1L76i&cid=228499695&page=1
date:       2020-08-24
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - 
---

### 题目

By now, you are given a secret signature consisting of character 'D' and 'I'. 'D' represents a decreasing relationship between two numbers, 'I' represents an increasing relationship between two numbers. And our secret signature was constructed by a special integer array, which contains uniquely all the different number from 1 to n (n is the length of the secret signature plus 1). For example, the secret signature "DI" can be constructed by array [2,1,3] or [3,1,2], but won't be constructed by array [3,2,4] or [2,1,3,4], which are both illegal constructing special string that can't represent the "DI" secret signature.

On the other hand, now your job is to find the lexicographically smallest permutation of [1, 2, ... n] could refer to the given secret signature in the input.

### 解题思路

贪心，首先创建一个1到n的排列，对于连续的D，将对应的区间进行翻转

### 代码
```python
class Solution:
    def findPermutation(self, s: str) -> List[int]:
        res = list(range(1, len(s) + 2))
        for m in re.finditer('D+', s):
            i, j = m.start(), m.end() + 1
            res[i: j] = res[i: j][::-1]
        return res
```
