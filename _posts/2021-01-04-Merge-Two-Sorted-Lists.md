---
layout:     post
title:      LeetCode 21 Merge Two Sorted Lists (Python)
number:     21
level:      Easy
lcurl:      merge-two-sorted-lists
youtube:    I5e5ZRSWC38
bilibili1:  //player.bilibili.com/player.html?aid=798563381&bvid=BV1my4y127bK&cid=277207031&page=1
xigua:      
date:       2020-01-04
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Linked List
---

### 题目

Merge two sorted linked lists and return it as a sorted list. The list should be made by splicing together the nodes of the first two lists.

### 解题思路

创建一个dummy的节点，同时遍历两个链表，每次把较小的放到后面，当一个链表结束之后，把另一个链表直接加到后面

### 代码
```python
class Solution:
    def mergeTwoLists(self, l1: ListNode, l2: ListNode) -> ListNode:
        dummy = ListNode(0)
        pre = dummy
        while l1 and l2:
            if l1.val < l2.val:
                pre.next = l1
                l1 = l1.next
            else:
                pre.next = l2
                l2 = l2.next
            pre = pre.next
        pre.next = l1 if l1 is not None else l2
        return dummy.next
```
