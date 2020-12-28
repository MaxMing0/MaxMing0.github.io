---
layout:     post
title:      LeetCode 24 Swap Nodes in Pairs (Python)
number:     24
level:      Medium
lcurl:      swap-nodes-in-pairs
youtube:    AWYgewYiZXI
bilibili1:  //player.bilibili.com/player.html?aid=203336225&bvid=BV1ih411f7YK&cid=272199692&page=1
xigua:      
date:       2020-12-28
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Linked List
---

### 题目

Given a linked list, swap every two adjacent nodes and return its head.

You may not modify the values in the list's nodes. Only nodes itself may be changed.

### 解题思路

创建一个dummy节点指向头，之后的结点两两交换

### 代码
```python
class Solution:
    def swapPairs(self, head: ListNode) -> ListNode:
        dummy = ListNode(0)
        res = dummy
        dummy.next = head
        while dummy.next and dummy.next.next:
            first = dummy.next
            second = dummy.next.next
            first.next = second.next
            second.next = first
            dummy.next = second
            dummy = dummy.next.next
        return res.next
```
