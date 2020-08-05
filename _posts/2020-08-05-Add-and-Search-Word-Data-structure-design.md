---
layout:     post
title:      LeetCode 211 Add and Search Word - Data structure design (Python)
number:     211
level:      Medium
lcurl:      add-and-search-word-data-structure-design
youtube:    UYsDWddmjVo
bilibili1:  //player.bilibili.com/player.html?aid=456551325&bvid=BV1x5411a77S&cid=220727402&page=1
xigua:      
date:       2020-08-05
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Trie
---

### 题目

Design a data structure that supports the following two operations:

- void addWord(word)
- bool search(word)

search(word) can search a literal word or a regular expression string containing only letters a-z or .. A . means it can represent any one letter.

### 解题思路

字典树，在查找的时候，使用dfs，如果遇到点，要遍历所有子树

### 代码
```python
class WordDictionary:

    def __init__(self):
        """
        Initialize your data structure here.
        """
        self.trie = {}

    def addWord(self, word: str) -> None:
        """
        Adds a word into the data structure.
        """
        cur = self.trie
        for c in word:
            if c not in cur:
                cur[c] = {}
            cur = cur[c]
        cur['#'] = True

    def search(self, word: str) -> bool:
        """
        Returns if the word is in the data structure. A word could contain the dot character '.' to represent any one letter.
        """
        return self.dfs(self.trie, word, 0)
    
    def dfs(self, node, word, i):
        if i == len(word):
            return '#' in node
        if word[i] == '.':
            for child in node:
                if child != '#' and self.dfs(node[child], word, i + 1):
                    return True
            return False
        
        if word[i] not in node:
            return False
        return self.dfs(node[word[i]], word, i + 1)
```
```python
class WordDictionary:

    def __init__(self):
        """
        Initialize your data structure here.
        """
        self.dic = defaultdict(set)

    def addWord(self, word: str) -> None:
        """
        Adds a word into the data structure.
        """
        self.dic[len(word)].add(word)

    def search(self, word: str) -> bool:
        """
        Returns if the word is in the data structure. A word could contain the dot character '.' to represent any one letter.
        """
        if '.' not in word:
            return word in self.dic[len(word)]
        for v in self.dic[len(word)]:
            for i, ch in enumerate(word):
                if ch != v[i] and ch != '.':
                    break
            else:
                return True
        return False

# Your WordDictionary object will be instantiated and called as such:
# obj = WordDictionary()
# obj.addWord(word)
# param_2 = obj.search(word)
```
