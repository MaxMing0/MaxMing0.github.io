---
layout:     post
title:      LeetCode 17 Letter Combinations of a Phone Number (Python)
number:     17
level:      Medium
lcurl:      letter-combinations-of-a-phone-number
youtube:    ruVKuEj4R6U
bilibili1:  //player.bilibili.com/player.html?aid=545035601&bvid=BV1Ti4y1A73M&cid=323899162&page=1
xigua:      
date:       2021-04-13
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - 
---

### 题目

Given a string containing digits from 2-9 inclusive, return all possible letter combinations that the number could represent. Return the answer in any order.

A mapping of digit to letters (just like on the telephone buttons) is given below. Note that 1 does not map to any letters.

### 解题思路

将当前的结果与新的数字所对应的字符进行拓展

### 代码
```python
class Solution:
    def letterCombinations(self, digits: str) -> List[str]:
        if not digits:
            return []
        dic = {'2':"abc", '3':"def", '4':"ghi", '5':"kjl", '6':"mno", '7':"pqrs", '8':"tuv", '9':"wxyz"}
        res = [c for c in dic[digits[0]]]
        for d in digits[1:]:
                res = [i + c for i in res for c in dic[d]]
        return res
```
