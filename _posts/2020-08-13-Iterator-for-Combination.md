---
layout:     post
title:      LeetCode 1286 Iterator for Combination (Python)
number:     1286
level:      Medium
lcurl:      iterator-for-combination
youtube:    ePnLx1rUve0
bilibili1:  //player.bilibili.com/player.html?aid=499134158&bvid=BV1TK411T7e6&cid=223964656&page=1
xigua:      
date:       2020-08-13
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Design
    - Backtracking
---

### 题目

Design an Iterator class, which has:

- A constructor that takes a string characters of sorted distinct lowercase English letters and a number combinationLength as arguments.
- A function next() that returns the next combination of length combinationLength in lexicographical order.
- A function hasNext() that returns True if and only if there exists a next combination.

### 解题思路

1. 使用递归求出所有的结果，python可以使用`yield from`来节省空间
2. 对于每个结果都对于一个二进制的数，如果这个数的1的个数为combinationLength，则是一个结果，从`2^L-1`开始遍历

### 代码
```python
from math import gamma
class CombinationIterator:

    def __init__(self, characters: str, combinationLength: int):
        l = len(characters)
        self.count = int(gamma(l + 1) / gamma(l - combinationLength + 1) / gamma(combinationLength + 1))
        self.wg = self.wordgen(characters, combinationLength)

    def next(self) -> str:
        self.count -= 1
        return next(self.wg)

    def hasNext(self) -> bool:
        return self.count > 0
    
    def wordgen(self, characters, combinationLength):
        if combinationLength == 1:
            yield from characters
        else:
            for i in range(len(characters) - combinationLength + 1):
                yield from (characters[i] + tail for tail in self.wordgen(characters[i+1:], combinationLength - 1))
```
```python
class CombinationIterator:

    def __init__(self, characters: str, combinationLength: int):
        self.s = characters[::-1]
        self.cur = (1 << len(characters)) - 1
        self.l = combinationLength

    def count(self, n):
        ret = 0
        while n:
            ret += 1
            n = n & (n - 1)
        return ret
    
    def next(self) -> str:
        while self.cur and self.count(self.cur) != self.l:
            self.cur -= 1
            
        res = []
        for i in range(len(self.s)):
            if (self.cur & (1<<i)) >> i:
                res.append(self.s[i])
        self.cur -= 1
        return ''.join(res)[::-1]

    def hasNext(self) -> bool:
        while self.cur and self.count(self.cur) != self.l:
            self.cur -= 1
        return self.cur > 0
```
