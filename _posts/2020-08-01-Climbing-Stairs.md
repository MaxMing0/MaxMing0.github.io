---
layout:     post
title:      LeetCode 520 Detect Capital (Python)
number:     520
level:      Easy
lcurl:      detect-capital
youtube:    xtZ5BIJzUXo
bilibili1:  //player.bilibili.com/player.html?aid=926531709&bvid=BV1xT4y1j7G4&cid=219141513&page=1
xigua:      
date:       2020-08-01
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - String
---

### 题目

Given a word, you need to judge whether the usage of capitals in it is right or not.

We define the usage of capitals in a word to be right when one of the following cases holds:

1. All letters in this word are capitals, like "USA".
2. All letters in this word are not capitals, like "leetcode".
3. Only the first letter in this word is capital, like "Google".
Otherwise, we define that this word doesn't use capitals in a right way.

### 解题思路

如果第一个字母是大写，如果只有一个字母为True，否则后面全大写或全小写，如果第一个字母是小写，则都要是小写

### 代码
```python
class Solution:
    def detectCapitalUse(self, word: str) -> bool:
        return word.isupper() or word.islower() or word.istitle()
```
```python
class Solution:
    def detectCapitalUse(self, word: str) -> bool:
        if word[0].isupper():
            if len(word)==1:
                return True
            else:
                if word[1].isupper():
                    for s in word[1:]:
                        if not s.isupper():
                            return False
                else:
                    for s in word[1:]:
                        if s.isupper():
                            return False
        else:
            for s in word[1:]:
                if s.isupper():
                    return False
        return True
```
