---
layout:     post
title:      LeetCode 880 Decoded String at Index (Python)
number:     880
level:      Medium
lcurl:      decoded-string-at-index
youtube:    3mFf8LVkoek
bilibili1:  //player.bilibili.com/player.html?aid=628154340&bvid=BV1Tt4y1k7GJ&cid=269116593&page=1
xigua:      
date:       2020-12-20
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - 
---

### 题目

An encoded string S is given.  To find and write the decoded string to a tape, the encoded string is read one character at a time and the following steps are taken:

- If the character read is a letter, that letter is written onto the tape.
- If the character read is a digit (say d), the entire current tape is repeatedly written d-1 more times in total.
Now for some encoded string S, and an index K, find and return the K-th letter (1 indexed) in the decoded string.

### 解题思路

先求出最后解码字符串的长度，从后向前遍历，遇到数字，长度除这个数，遇到字母长度减一，并且每次用k对size取模。一个优化，如果在中间长度已经大于k了，就结束在这里，开始向前做。

### 代码
```python
class Solution:
    def decodeAtIndex(self, S: str, K: int) -> str:
        size = 0
        for i, c in enumerate(S):
            if c.isdigit():
                size *= int(c)
            else:
                size += 1
            if K <= size:
                break
        for c in S[i::-1]:
            if c.isdigit():
                size /= int(c)
                K %= size
            else:
                if K % size == 0:
                    return c
                size -= 1
```
