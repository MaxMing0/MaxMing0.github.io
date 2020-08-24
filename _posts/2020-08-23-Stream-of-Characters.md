---
layout:     post
title:      LeetCode 1032 Stream of Characters (Python)
number:     1032
level:      Hard
lcurl:      stream-of-characters
youtube:    nlfunbuvjQY
bilibili1:  //player.bilibili.com/player.html?aid=926828533&bvid=BV15T4y1L7RG&cid=227941714&page=1
xigua:      
date:       2020-08-23
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Trie
---

### 题目

Implement the StreamChecker class as follows:

- StreamChecker(words): Constructor, init the data structure with the given words.
- query(letter): returns true if and only if for some k >= 1, the last k characters queried (in order from oldest to newest, including this letter just queried) spell one of the words in the given list.

### 解题思路

使用字典树，建树的时候，把单词翻转，这样每次query的时候，同样返现查找，这样一次字典树的搜索，就可以查询从任何一个位置开始，到当前字符组成的单词是否出现过

### 代码
```python
class Trie:
    def __init__(self):
        """ Initialize your data structure here. """
        self.dic = {}

    def insert(self, word: str) -> None:
        """ Inserts a word into the trie. """
        cur = self.dic
        for c in word:
            if c not in cur:
                cur[c] = {}
            cur = cur[c]
        cur['#'] = True
        
    def search(self, word: list) -> bool:
        """ Returns if the word is in the trie. """
        cur = self.dic
        for c in word:
            if '#' in cur:
                return True
            if c not in cur:
                return False
            cur = cur[c]
        return '#' in cur
    
class StreamChecker:

    def __init__(self, words: List[str]):
        self.trie = Trie()
        for w in words:
            self.trie.insert(w[::-1])
        self.s = deque()

    def query(self, letter: str) -> bool:
        self.s.appendleft(letter)
        return self.trie.search(self.s)


# Your StreamChecker object will be instantiated and called as such:
# obj = StreamChecker(words)
# param_1 = obj.query(letter)
```
