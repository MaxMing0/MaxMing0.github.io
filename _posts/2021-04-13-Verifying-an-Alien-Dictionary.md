---
layout:     post
title:      LeetCode 953 Verifying an Alien Dictionary (Python)
number:     953
level:      Easy
lcurl:      verifying-an-alien-dictionary
youtube:    kx3D8UqTcnA
bilibili1:  //player.bilibili.com/player.html?aid=757537414&bvid=BV1C64y1S7tT&cid=323904892&page=1
xigua:      
date:       2021-04-13
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Hash
---

### 题目

In an alien language, surprisingly they also use english lowercase letters, but possibly in a different order. The order of the alphabet is some permutation of lowercase letters.

Given a sequence of words written in the alien language, and the order of the alphabet, return true if and only if the given words are sorted lexicographicaly in this alien language.

### 解题思路

将字母表存到字典中，相邻的两个字符串依次比较，判断是否符合要求，要处理两个单词一个是另外一个的前缀

### 代码
```python
class Solution:
    def isAlienSorted(self, words: List[str], order: str) -> bool:
        dic = {c: i for i, c in enumerate(order)}
        for i in range(len(words) - 1):
            word1 = words[i]
            word2 = words[i + 1]
            for k in range(min(len(word1), len(word2))):
                if word1[k] != word2[k]:
                    if dic[word1[k]] > dic[word2[k]]:
                        return False
                    break
            else:
                if len(word1) > len(word2):
                    return False
        return True
```
