---
layout:     post
title:      LeetCode 206 Reverse Linked List (Python)
number:     206
level:      Easy
lcurl:      reverse-linked-list
youtube:    hrNGku4_uZE
bilibili1:  
xigua:      
date:       2022-3-16
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Recursive
---

### 题目

Given the head of a singly linked list, reverse the list, and return the reversed list.

### 解题思路

递归和非递归两种方法

### 代码
```python
class Solution:
    def reverseList(self, head: Optional[ListNode]) -> Optional[ListNode]:
        if not head or not head.next:
            return head
        p = self.reverseList(head.next)
        head.next.next = head
        head.next = None
        return p
```
```python
class Solution:
    def reverseList(self, head: Optional[ListNode]) -> Optional[ListNode]:
        pre = None
        cur = head
        while cur:
            t = cur.next
            cur.next = pre
            pre = cur
            cur = t
        return pre
```
