---
layout:     post
title:      LeetCode 430 Flatten a Multilevel Doubly Linked List (Python)
number:     430
level:      Medium
lcurl:      flatten-a-multilevel-doubly-linked-list
youtube:    3R151vu1vB0
bilibili1:  //player.bilibili.com/player.html?aid=841294951&bvid=BV1754y1q7Kb&cid=210925404&page=1
xigua:      
date:       2020-07-10
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Linked List
    - Stack
---

### 题目

You are given a doubly linked list which in addition to the next and previous pointers, it could have a child pointer, which may or may not point to a separate doubly linked list. These child lists may have one or more children of their own, and so on, to produce a multilevel data structure, as shown in the example below.

Flatten the list so that all the nodes appear in a single-level, doubly linked list. You are given the head of the first level of the list.

### 解题思路

使用栈，压栈的顺序是先next再child，压child之后，把child变成空，需要一个dummyhead和pre来帮助建成新的链表

### 代码
```python
class Solution:
    def flatten(self, head: 'Node') -> 'Node':
        if not head:
            return
        dummy = Node(0,None,head,None)
        pre = dummy
        stack = [head]
        while stack:
            cur = stack.pop()
            if cur.next:
                stack.append(cur.next)
            if cur.child:
                stack.append(cur.child)
                cur.child = None
            cur.prev = pre
            pre.next = cur
            pre = cur
        dummy.next.prev = None
        return dummy.next
```
