---
layout:     post
title:      LeetCode 394 Decode String (Python)
number:     394
level:      Medium
lcurl:      decode-string
youtube:    nJAUGsu2kik
bilibili1:  //player.bilibili.com/player.html?aid=457756693&bvid=BV145411V75E&cid=257467979&page=1
xigua:      
date:       2020-11-19
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Stack
---

### 题目

Given an encoded string, return its decoded string.

The encoding rule is: k[encoded_string], where the encoded_string inside the square brackets is being repeated exactly k times. Note that k is guaranteed to be a positive integer.

You may assume that the input string is always valid; No extra white spaces, square brackets are well-formed, etc.

Furthermore, you may assume that the original data does not contain any digits and that digits are only for those repeat numbers, k. For example, there won't be input like 3a or 2[4].

### 解题思路

使用栈，每次遇到左括号之后，将当前的数和字母压栈，遇到右括号出栈，并将当前的字符重复栈中数字的次数，并与之前的字符串进行连接

### 代码
```python
class Solution:
    def decodeString(self, s: str) -> str:
        stack = []
        cur_num = cur_str = ''
        for c in s:
            if c == '[':
                stack.append(cur_str)
                stack.append(int(cur_num))
                cur_num = cur_str = ''
            elif c == ']':
                num = stack.pop()
                prev_str = stack.pop()
                cur_str = prev_str + cur_str * num
            elif c.isdigit():
                cur_num += c
            else:
                cur_str += c
        return cur_str
```
