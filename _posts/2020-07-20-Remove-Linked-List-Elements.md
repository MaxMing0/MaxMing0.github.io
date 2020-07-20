---
layout:     post
title:      LeetCode 203 Remove Linked List Elements (Python)
number:     203
level:      Easy
lcurl:      remove-linked-list-elements
youtube:    3_q6QroxJeM
bilibili1:  //player.bilibili.com/player.html?aid=541440730&bvid=BV1Yi4y137WA&cid=214578365&page=1
xigua:      
date:       2020-07-20
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Linked List
---

### 题目

Remove all elements from a linked list of integers that have value val.

### 解题思路

一个dummy节点指向头，维护一个cur节点，每当他下一个节点为要删除的数时，删除下一个节点，直到当前结点为最后一个

### 代码
```python
class Solution:
    def removeElements(self, head: ListNode, val: int) -> ListNode:
        dummy = ListNode(0)
        dummy.next = head
        cur = dummy
        while cur.next:
            if cur.next.val == val:
                cur.next = cur.next.next
            else:
                cur = cur.next
        return dummy.next
```
