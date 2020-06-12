---
layout:     post
title:      LeetCode 380 Insert Delete GetRandom O(1) (Python)
number:     380
level:      Medium
lcurl:      insert-delete-getrandom-o1
youtube:    
bilibili1:  
xigua:      
date:       2020-06-12
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Design
    - Hash
---

### 题目

Design a data structure that supports all following operations in average O(1) time.

1. insert(val): Inserts an item val to the set if not already present.
2. remove(val): Removes an item val from the set if present.
3. getRandom: Returns a random element from current set of elements. Each element must have the same probability of being returned.

### 解题思路

同时使用字典和列表，字典的key为给的值，val为其在list中的index，插入的时候同时插入到两个数据结构中，随机就直接在list中随机，删除则需要先将这个数与列表中的最后一个数交换，再删除

### 代码
```python
class RandomizedSet:

    def __init__(self):
        """
        Initialize your data structure here.
        """
        self.list = []
        self.dic = {}

    def insert(self, val: int) -> bool:
        """
        Inserts a value to the set. Returns true if the set did not already contain the specified element.
        """
        if val in self.dic:
            return False
        self.dic[val] = len(self.list)
        self.list.append(val)
        return True

    def remove(self, val: int) -> bool:
        """
        Removes a value from the set. Returns true if the set contained the specified element.
        """
        if val not in self.dic:
            return False
        last, idx = self.list[-1], self.dic[val]
        self.list[idx], self.dic[last] = last, idx
        del self.list[-1]
        del self.dic[val]
        return True

    def getRandom(self) -> int:
        """
        Get a random element from the set.
        """
        return random.choice(self.list)
```
