---
layout:     post
title:      LeetCode 344 Reverse String (Python)
number:     344
level:      Easy
lcurl:      reverse-string
youtube:    https://youtu.be/bSfzGLR0O2Q
bilibili1:  //player.bilibili.com/player.html?aid=795994156&bvid=BV1nC4y1a7DR&cid=198538665&page=1
xigua:      
date:       2020-06-04
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - String
---

### 题目

Write a function that reverses a string. The input string is given as an array of characters char[].

Do not allocate extra space for another array, you must do this by modifying the input array in-place with O(1) extra memory.

You may assume all the characters consist of printable ascii characters.

### 解题思路

1. 使用两个指针，指向头尾字符，进行交换，头指针+1，尾指针-1
2. 使用一个指针，第`i`个字符要和第`-i-1`个字符交换

### 代码
```python
# two pointers
class Solution:
    def reverseString(self, s: List[str]) -> None:
        """
        Do not return anything, modify s in-place instead.
        """
        l, r = 0, len(s) - 1
        while l < r:
            s[l], s[r] = s[r], s[l]
            l += 1
            r -= 1

# one pointer
class Solution:
    def reverseString(self, s: List[str]) -> None:
        """
        Do not return anything, modify s in-place instead.
        """
        for i in range(len(s) // 2):
            s[i], s[-i - 1] = s[-i - 1], s[i]
```
