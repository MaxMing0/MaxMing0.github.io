---
layout:     post
title:      LeetCode 126 Word Ladder II (Python)
number:     126
level:      Hard
lcurl:      word-ladder-ii
youtube:    QMNY5Xq8lO0
bilibili1:  
xigua:      
date:       2022-02-06
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - BFS
---

### 题目

A transformation sequence from word beginWord to word endWord using a dictionary wordList is a sequence of words beginWord -> s1 -> s2 -> ... -> sk such that:

Every adjacent pair of words differs by a single letter.
Every si for 1 <= i <= k is in wordList. Note that beginWord does not need to be in wordList.
sk == endWord
Given two words, beginWord and endWord, and a dictionary wordList, return all the shortest transformation sequences from beginWord to endWord, or an empty list if no such sequence exists. Each sequence should be returned as a list of the words [beginWord, s1, s2, ..., sk].

### 解题思路

先预处理，把每个单词的每一位换成下划线，相同的放到字典里，之后从beginword开始进行bfs找到所有路径

### 代码
```python
class Solution:
    def findLadders(self, beginWord: str, endWord: str, wordList: List[str]) -> List[List[str]]:
        wordList = set(wordList)
        res = []
        edge = defaultdict(list)
        for word in wordList:
            for i in range(len(word)):
                edge[word[:i] + "_" + word[i+1:]].append(word)
                
        q = {beginWord: [[beginWord]]}
        while q:
            wordList -= set(q.keys())
            new_q = collections.defaultdict(list)
            for w in q:
                if w == endWord: 
                    res += q[w]
                else:
                    for i in range(len(w)):
                        for neww in edge[w[:i] + "_" + w[i+1:]]:
                            if neww in wordList:
                                new_q[neww] += [j + [neww] for j in q[w]]          
            q = new_q
        return res
```
