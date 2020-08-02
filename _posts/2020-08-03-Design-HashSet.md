---
layout:     post
title:      LeetCode 705 Design HashSet (Python)
number:     705
level:      Easy
lcurl:      design-hashset
youtube:    UusZnTKeW1I
bilibili1:  //player.bilibili.com/player.html?aid=414113111&bvid=BV1hV411z73p&cid=219552170&page=1
xigua:      
date:       2020-08-02
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Design
---

### 题目

Design a HashSet without using any built-in hash table libraries.

To be specific, your design should include these functions:

- add(value): Insert a value into the HashSet. 
- contains(value) : Return whether the value exists in the HashSet or not.
- remove(value): Remove a value in the HashSet. If the value does not exist in the HashSet, do nothing.

### 解题思路

哈希函数对一个质数取余，用链接法解决冲突，bucket用链表实现

### 代码
```python
class Node:
    
    def __init__(self, value, nextNode=None):
        self.val = value
        self.next = nextNode
        
class Bucket:
    
    def __init__(self):
        self.head = Node(0)
    
    def exists(self, val):
        cur = self.head.next
        while cur:
            if cur.val == val:
                return True
            cur = cur.next
        return False
    
    def insert(self, val):
        if not self.exists(val):
            node = Node(val, self.head.next)
            self.head.next = node
            
    def delete(self, val):
        pre = self.head
        cur = self.head.next
        while cur:
            if cur.val == val:
                pre.next = cur.next
                return
            pre = cur
            cur = cur.next
    
class MyHashSet:

    def __init__(self):
        """
        Initialize your data structure here.
        """
        self.m = 1009
        self.bucket = [Bucket() for i in range(self.m)]

    def _hash(self, key):
        return key % self.m
    
    def add(self, key: int) -> None:
        self.bucket[self._hash(key)].insert(key)

    def remove(self, key: int) -> None:
        self.bucket[self._hash(key)].delete(key)

    def contains(self, key: int) -> bool:
        """
        Returns true if this set contains the specified element
        """
        return self.bucket[self._hash(key)].exists(key)
```
