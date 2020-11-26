---
layout:     post
title:      LeetCode 395 Longest Substring with At Least K Repeating Characters (Python)
number:     395
level:      Medium
lcurl:      longest-substring-with-at-least-k-repeating-characters
youtube:    izjPlJrZ_K0
bilibili1:  //player.bilibili.com/player.html?aid=712908815&bvid=BV1hD4y1X7rq&cid=259970933&page=1
xigua:      
date:       2020-11-26
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Sliding Window
---

### 题目

Given a string s and an integer k, return the length of the longest substring of s such that the frequency of each character in this substring is less than or equal to k.

### 解题思路

Sliding Window， 枚举答案子串中出现的不同字母的个数，然后维护当前有多少个不同的字母，以及有多少个字母出现的次数是k次，如果这两个数都是最开始假设的不同字母个数，就是一个可行解，更新结果

### 代码
```python
class Solution:
    def longestSubstring(self, s: str, k: int) -> int:
        res = 0
        for i in range(1, len(set(s)) + 1):
            times = [0] * 26
            l = r = ct = dif_ct = 0
            while r < len(s):
                ind = ord(s[r]) - ord('a')
                times[ind] += 1
                if times[ind] == 1:
                    dif_ct += 1
                if times[ind] == k:
                    ct += 1
                r += 1
                
                while l < r and dif_ct > i:
                    ind = ord(s[l]) - ord('a')
                    if times[ind] == k:
                        ct -= 1
                    if times[ind] == 1:
                        dif_ct -= 1
                    times[ind] -= 1
                    l += 1
                if dif_ct == ct == i:
                    res = max(res, r - l)
        return res
```
