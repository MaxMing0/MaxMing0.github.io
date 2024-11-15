---
layout:     post
title:      LeetCode 21 Merge Two Sorted Lists (Python)
number:     21
level:      Easy
lcurl:      merge-two-sorted-lists
youtube:    
bilibili1:  
xigua:      
date:       2024-11-14
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Linked List
---

### 题目

You are given the heads of two sorted linked lists list1 and list2.

Merge the two lists into one sorted list. The list should be made by splicing together the nodes of the first two lists.

Return the head of the merged linked list.

### 解题思路

创建一个虚拟节点指向结果，两个指针，每次将较小的数，连接到结果

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
