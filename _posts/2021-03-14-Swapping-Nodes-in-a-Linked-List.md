---
layout:     post
title:      LeetCode 1721 Swapping Nodes in a Linked List (Python)
number:     1721
level:      Medium
lcurl:      swapping-nodes-in-a-linked-list
youtube:    wScPGCOGZ60
bilibili1:  //player.bilibili.com/player.html?aid=544749232&bvid=BV1Ji4y1P7Xc&cid=310503343&page=1
xigua:      
date:       2021-03-14
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Linked List
---

### 题目

You are given the head of a linked list, and an integer k.

Return the head of the linked list after swapping the values of the kth node from the beginning and the kth node from the end (the list is 1-indexed).

### 解题思路

第一个指针先移动到第k个位置，之后第二个指针从头开始一起移动，第一个指针到末尾的时候，第二个指针在倒数第k个，交换两个指针的值

### 代码
```python
class Solution:
    def swapNodes(self, head: ListNode, k: int) -> ListNode:
        first = head
        for i in range(k - 1):
            first = first.next
        tmp = first
        second = head
        while first.next:
            first = first.next
            second = second.next
        tmp.val, second.val = second.val, tmp.val
        return head
```
