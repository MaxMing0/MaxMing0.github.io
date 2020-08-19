---
layout:     post
title:      LeetCode 824 Goat Latin (Python)
number:     824
level:      Easy
lcurl:      goat-latin
youtube:    glJFT0uFk-U
bilibili1:  //player.bilibili.com/player.html?aid=201838312&bvid=BV1Th411o782&cid=226263412&page=1
xigua:      
date:       2020-08-19
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - String
---

### 题目

A sentence S is given, composed of words separated by spaces. Each word consists of lowercase and uppercase letters only.

We would like to convert the sentence to "Goat Latin" (a made-up language similar to Pig Latin.)

The rules of Goat Latin are as follows:

- If a word begins with a vowel (a, e, i, o, or u), append "ma" to the end of the word.
For example, the word 'apple' becomes 'applema'.
 
- If a word begins with a consonant (i.e. not a vowel), remove the first letter and append it to the end, then add "ma".
For example, the word "goat" becomes "oatgma".
 
- Add one letter 'a' to the end of each word per its word index in the sentence, starting with 1.
For example, the first word gets "a" added to the end, the second word gets "aa" added to the end and so on.
Return the final sentence representing the conversion from S to Goat Latin. 

### 解题思路

按照题目要求模拟

### 代码
```python
class Solution:
    def toGoatLatin(self, S: str) -> str:
        res = []
        for i, word in enumerate(S.split()):
            if word[0].lower() in ('aeiou'):
                res.append(word + "ma" + "a" * (i + 1))
            else:
                res.append(word[1:] + word[0] + "ma" + "a" * (i + 1))
        return ' '.join(res)
```
