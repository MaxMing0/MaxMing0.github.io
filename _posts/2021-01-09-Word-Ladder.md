---
layout:     post
title:      LeetCode 127 Word Ladder (Python)
number:     127
level:      Hard
lcurl:      word-ladder
youtube:    ntzcXQZ12H8
bilibili1:  //player.bilibili.com/player.html?aid=886031169&bvid=BV1BK4y157k1&cid=280444419&page=1
xigua:      
date:       2020-01-09
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - BFS
---

### 题目

Given two words beginWord and endWord, and a dictionary wordList, return the length of the shortest transformation sequence from beginWord to endWord, such that:

- Only one letter can be changed at a time.
- Each transformed word must exist in the word list.
Return 0 if there is no such transformation sequence.

### 解题思路

将单词的每一个位置替换成一个符号，这样就可以快速找到相邻的单词，只看从开始结束位置进行双向bfs

### 代码
```python
class Solution:
    def ladderLength(self, beginWord: str, endWord: str, wordList: List[str]) -> int:
        wordList = set(wordList)
        if endWord not in wordList:
            return 0
        wordList.add(beginWord)
        l = len(beginWord)
        dic = defaultdict(list)
        for word in wordList:
            for i in range(l):
                tmp = word[:i] + '_' + word[i + 1:]
                dic[tmp].append(word)
        q1 = deque([beginWord])
        dis1 = {w: 0 for w in wordList}
        dis1[beginWord] = 1
        q2 = deque([endWord])
        dis2 = {w: 0 for w in wordList}
        dis2[endWord] = 1
        flag = True
        while q1 and q2:
            if flag:
                front, dis_front = q1, dis1
                back, dis_back = q2, dis2
            else:
                front, dis_front = q2, dis2
                back, dis_back = q1, dis1 
            cur = front.popleft()
            dist = dis_front[cur]
            next_word = []
            for i in range(l):
                tmp = cur[:i] + '_' + cur[i + 1:]
                for w in dic[tmp]:
                    next_word.append(w)
            for w in next_word:
                if dis_back[w] > 0:
                    return dist + dis_back[w]
                if dis_front[w] == 0:
                    dis_front[w] = dist + 1
                    front.append(w)
            if len(back) < len(front):
                flag = not flag
        return 0
```
