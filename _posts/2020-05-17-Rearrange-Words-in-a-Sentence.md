---
layout:     post
title:      LeetCode 1451 Rearrange Words in a Sentence (Python)
number:     1451
level:      Medium
lcurl:      rearrange-words-in-a-sentence
youtube:    3zL_4D8Sc1Q
bilibili1:  //player.bilibili.com/player.html?aid=328187129&bvid=BV1UA411t7Eg&cid=192308298&page=1
xigua:      
date:       2020-05-17
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Sort
---

### 题目

Given a sentence text (A sentence is a string of space-separated words) in the following format:

- First letter is in upper case.
- Each word in text are separated by a single space.
Your task is to rearrange the words in text such that all words are rearranged in an increasing order of their lengths. If two words have the same length, arrange them in their original order.

Return the new text following the format shown above.

### 解题思路

先split出每个单词，按单词数排序，拼回去再把首字母大写

### 代码
```python
class Solution:
    def arrangeWords(self, text: str) -> str:
        return " ".join(sorted(text.split(), key=len)).capitalize()
```
