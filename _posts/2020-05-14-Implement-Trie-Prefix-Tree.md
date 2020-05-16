---
layout:     post
title:      LeetCode 208 Implement Trie (Prefix Tree) (Python)
number:     208
level:      Medium
lcurl:      implement-trie-prefix-tree
youtube:    vSA1_aJfYsk
bilibili1:  //player.bilibili.com/player.html?aid=583142782&bvid=BV1Zz4y1R7j8&cid=190905824&page=1
xigua:      
date:       2020-05-14
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Trie
    - Design
---

### 题目

Implement a trie with insert, search, and startsWith methods.

### 解题思路

字典树的每一个节点都是一个map，key是当前字母，value是所有的子树，如果一个单词结束，就在下方插入一个`#`作为标记

### 代码
```python
class Trie:
    def __init__(self):
        """
        Initialize your data structure here.
        """
        self.dic = {}

    def insert(self, word: str) -> None:
        """
        Inserts a word into the trie.
        """
        cur = self.dic
        for c in word:
            if c not in cur:
                cur[c] = {}
            cur = cur[c]
        cur['#'] = True

    def search(self, word: str) -> bool:
        """
        Returns if the word is in the trie.
        """
        cur = self.dic
        for c in word:
            if c not in cur:
                return False
            cur = cur[c]
        return '#' in cur

    def startsWith(self, prefix: str) -> bool:
        """
        Returns if there is any word in the trie that starts with the given prefix.
        """
        cur = self.dic
        for c in prefix:
            if c not in cur:
                return False
            cur = cur[c]
        return True
```
