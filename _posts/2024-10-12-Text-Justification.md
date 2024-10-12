---
layout:     post
title:      LeetCode 68 Text Justification (Python)
number:     68
level:      Hard
lcurl:      text-justification
youtube:    
bilibili1:  
xigua:      
date:       2024-10-12
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - String
---

### 题目

Given an array of strings words and a width maxWidth, format the text such that each line has exactly maxWidth characters and is fully (left and right) justified.

You should pack your words in a greedy approach; that is, pack as many words as you can in each line. Pad extra spaces ' ' when necessary so that each line has exactly maxWidth characters.

Extra spaces between words should be distributed as evenly as possible. If the number of spaces on a line does not divide evenly between words, the empty slots on the left will be assigned more spaces than the slots on the right.

For the last line of text, it should be left-justified, and no extra space is inserted between words.

Note:

- A word is defined as a character sequence consisting of non-space characters only.
- Each word's length is guaranteed to be greater than 0 and not exceed maxWidth.
- The input array words contains at least one word.

### 解题思路

模拟，使用一个数组存储当前所有遇到的单词，如果在加入下一个单词后会超过长度，那么当前的所有单词会变成一行。

如果只有一个单词，就放在最前面，否则需要计算单词直接需要插入几个空格，要平均，多出来的位置前几个单词后面多加一个空格

最后一行单独处理，单词之间只需要一个空格

### 代码
```python
class Solution:
    def fullJustify(self, words: List[str], maxWidth: int) -> List[str]:
        res, cur, numLetter = [], [], 0
        for word in words:
            if numLetter + len(word) + len(cur) > maxWidth:
                if len(cur) == 1:
                    res.append(cur[0] + ' ' * (maxWidth - numLetter))
                else:
                    space = maxWidth - numLetter
                    gap, extra = divmod(space, len(cur) - 1)
                    for i in range(extra):
                        cur[i] += ' '
                    res.append((' ' * gap).join(cur))
                cur, numLetter = [], 0
            cur.append(word)
            numLetter += len(word)
        res.append(' '.join(cur) + ' ' * (maxWidth - numLetter - len(cur) + 1))
        return res
```
