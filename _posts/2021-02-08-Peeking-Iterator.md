---
layout:     post
title:      LeetCode 284 Peeking Iterator (Python)
number:     284
level:      Medium
lcurl:      peeking-iterator
youtube:    evNDFy6Gtg0
bilibili1:  //player.bilibili.com/player.html?aid=501569712&bvid=BV1LN411R7U7&cid=295179633&page=1
xigua:      
date:       2021-02-08
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Design
---

### 题目

Given an Iterator class interface with methods: next() and hasNext(), design and implement a PeekingIterator that support the peek() operation -- it essentially peek() at the element that will be returned by the next call to next().

### 解题思路

记录当前的peek，next会返回当前的peek，并且更新peek为下一个数

### 代码
```python
class PeekingIterator:
    def __init__(self, iterator):
        """
        Initialize your data structure here.
        :type iterator: Iterator
        """
        self.it = iterator
        self.peeknum = self.it.next() if self.it.hasNext() else None

    def peek(self):
        """
        Returns the next element in the iteration without advancing the iterator.
        :rtype: int
        """
        return self.peeknum

    def next(self):
        """
        :rtype: int
        """
        ret = self.peeknum
        self.peeknum = self.it.next() if self.it.hasNext() else None
        return ret

    def hasNext(self):
        """
        :rtype: bool
        """
        return self.peeknum is not None
```
