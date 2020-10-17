---
layout:     post
title:      LeetCode 187 Repeated DNA Sequences (Python)
number:     187
level:      Medium
lcurl:      repeated-dna-sequences
youtube:    L7NiYdYxmYQ
bilibili1:  //player.bilibili.com/player.html?aid=969961953&bvid=BV1mp4y1r7v5&cid=246590617&page=1
xigua:      
date:       2020-10-17
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Hash
---

### 题目

All DNA is composed of a series of nucleotides abbreviated as 'A', 'C', 'G', and 'T', for example: "ACGAATTCCG". When studying DNA, it is sometimes useful to identify repeated sequences within the DNA.

Write a function to find all the 10-letter-long sequences (substrings) that occur more than once in a DNA molecule.

### 解题思路

对于每个子串，存到set中，如果出现过，则加到结果里。可以使用RK算法进行哈希，降低复杂度，可以参考LeetCode 1044 Longest Duplicate Substring[Leetcode1044](https://maxming0.github.io/2020/06/19/Longest-Duplicate-Substring/)

### 代码
```python
class Solution:
    def findRepeatedDnaSequences(self, s: str) -> List[str]:
        seen = set()
        res = set()
        for i in range(len(s) - 9):
            tmp=s[i: i + 10]
            if tmp in seen:
                res.add(tmp)
            else:
                seen.add(tmp)
        return res
```
```python
class Solution:
    def findRepeatedDnaSequences(self, s: str) -> List[str]:
        L, n = 10, len(s)
        if n <= L:
            return []
        a = 4
        MOD = 2 ** 63 - 1
        aL = pow(a, L, MOD)
        to_int = {'A': 0, 'C': 1, 'G': 2, 'T': 3}
        nums = [to_int[s[i]] for i in range(n)]
        h = 0
        for i in range(L):
            h = h * a + nums[i]
        seen, res = {h, }, set()
        for i in range(1, n - L + 1):
            h = (h * a - nums[i - 1] * aL + nums[i + L - 1]) % MOD
            if h in seen:
                res.add(s[i: i + L])
            else:
                seen.add(h)
        return res
```
