---
layout:     post
title:      LeetCode 125 Valid Palindrome (Python)
number:     125
level:      Easy
lcurl:      valid-palindrome
youtube:    U8KklSWj6eo
bilibili1:  //player.bilibili.com/player.html?aid=201542770&bvid=BV17h411Z7ey&cid=219915385&page=1
xigua:      
date:       2020-08-03
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - String
---

### 题目

Given a string, determine if it is a palindrome, considering only alphanumeric characters and ignoring cases.

Note: For the purpose of this problem, we define empty string as valid palindrome.

### 解题思路

和普通的判断字符串是否为回文一样，l r两个指针，每次在比较之前，先跳掉所有非字母或数字的字符

### 代码
```python
class Solution:
    def isPalindrome(self, s: str) -> bool:
        l, r = 0, len(s) - 1
        while l < r:
            while l < r and not s[l].isalnum():
                l += 1
            while l < r and not s[r].isalnum():
                r -= 1
            if l < r:
                if s[l].lower() != s[r].lower():
                    return False
                l += 1
                r -= 1
        return True
```
