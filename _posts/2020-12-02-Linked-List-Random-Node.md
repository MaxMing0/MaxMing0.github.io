---
layout:     post
title:      LeetCode 382 Linked List Random Node (Python)
number:     382
level:      Medium
lcurl:      maximum-depth-of-binary-tree
youtube:    EZTRRVOT2BM
bilibili1:  //player.bilibili.com/player.html?aid=372934024&bvid=BV1xZ4y1G7ie&cid=262078806&page=1
xigua:      
date:       2020-12-02
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Reservoir Sampling
---

### 题目

Given a singly linked list, return a random node's value from the linked list. Each node must have the same probability of being chosen.

Follow up:
What if the linked list is extremely large and its length is unknown to you? Could you solve this efficiently without using extra space?

### 解题思路

[水塘抽样](https://zh.wikipedia.org/zh-cn/%E6%B0%B4%E5%A1%98%E6%8A%BD%E6%A8%A3)

### 代码
```python
class Solution:

    def __init__(self, head: ListNode):
        """
        @param head The linked list's head.
        Note that the head is guaranteed to be not null, so it contains at least one node.
        """
        self.head = head
        

    def getRandom(self) -> int:
        """
        Returns a random node's value.
        """
        count = res = 0
        cur = self.head
        while cur:
            count += 1
            if random.random() <= 1 / count:
                res = cur.val
            cur = cur.next
        return res
```
