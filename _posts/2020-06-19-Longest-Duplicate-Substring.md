---
layout:     post
title:      LeetCode 1044 Longest Duplicate Substring (Python)
number:     1044
level:      Hard
lcurl:      longest-duplicate-substring
youtube:    bwgJS7lKFSY
bilibili1:  
xigua:      
date:       2020-06-19
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Binary Search
---

### 题目

Given a string S, consider all duplicated substrings: (contiguous) substrings of S that occur 2 or more times.  (The occurrences may overlap.)

Return any duplicated substring that has the longest possible length.  (If S does not have a duplicated substring, the answer is "".)

### 解题思路

二分答案，当每次确定了解的长度之后，判断这个长度的所有子串是否有重复出现，判断的时候使用 
[Rabin–Karp算法](https://zh.wikipedia.org/zh-cn/Rabin%E2%80%93Karp%E7%AE%97%E6%B3%95)

具体请看下方视频

### 代码
```python
class Solution:
    def longestDupSubstring(self, S: str) -> str:
        def search(m, MOD):
            h = 0
            for i in range(m):
                h = (h * 26 + nums[i]) % MOD
            s = {h}
            aL = pow(26, m, MOD)
            for pos in range(1, n - m + 1):
                h = (h * 26 - nums[pos - 1] * aL + nums[pos + m - 1]) % MOD
                if h in s:
                    return pos
                s.add(h)
            return -1

        n = len(S)
        nums = [ord(c) - ord('a') for c in S]
        l, r = 1, n
        pos = -1
        MOD = 2**63 - 1
        while l <= r:
            m = (l + r) // 2
            cur = search(m, MOD)
            if cur != -1:
                l = m + 1
                pos = cur
            else:
                r = m - 1
        return S[pos: pos + l - 1]
```
