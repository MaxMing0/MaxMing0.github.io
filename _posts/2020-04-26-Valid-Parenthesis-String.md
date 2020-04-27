---
layout:     post
title:      LeetCode 678 Valid Parenthesis String (Python)
number:     678
level:      Medium
lcurl:      valid-parenthesis-string
youtube:    JNip3SgpZok
bilibili1:  //player.bilibili.com/player.html?aid=967866494&bvid=BV1ap4y1X7nu&cid=179147524&page=1
xigua:      
date:       2020-04-26
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - String
---

### 题目
Given a string containing only three types of characters: '(', ')' and '*', write a function to check whether this string is valid. We define the validity of a string by these rules:

1. Any left parenthesis '(' must have a corresponding right parenthesis ')'.
2. Any right parenthesis ')' must have a corresponding left parenthesis '('.
3. Left parenthesis '(' must go before the corresponding right parenthesis ')'.
4. '*' could be treated as a single right parenthesis ')' or a single left parenthesis '(' or an empty string.
5. An empty string is also valid.


### 解题思路



### 代码
```python
class Solution:
    def checkValidString(self, s: str) -> bool:
        l = r = 0
        for c in s:
            if c == '(':
                l += 1
                r += 1
            elif c == ')':
                if l > 0:
                    l -= 1
                r -= 1
            else:
                if l > 0:
                    l -= 1
                r += 1
            if r < 0:
                return False
        return l == 0
```