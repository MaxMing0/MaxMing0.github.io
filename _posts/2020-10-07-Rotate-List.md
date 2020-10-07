---
layout:     post
title:      LeetCode 61 Rotate List (Python)
number:     61
level:      Medium
lcurl:      rotate-list
youtube:    Q2-R-e9XCVM
bilibili1:  //player.bilibili.com/player.html?aid=499820754&bvid=BV1jK411N7e6&cid=243151705&page=1
xigua:      
date:       2020-10-07
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Linked List
---

### 题目

Given a linked list, rotate the list to the right by k places, where k is non-negative.

### 解题思路

首先将将链表变成环，同时计算出一共有多少个结点，然后移动到`(n-k%n-1)`这个节点，其后一个节点为结果，并把这个节点的`next`指针变为空

### 代码
```python
class Solution:
    def rotateRight(self, head: ListNode, k: int) -> ListNode:
        if not head or not head.next: 
            return head
        
        tail = head
        n = 1
        while head.next :
            head = head.next
            n += 1
        head.next = tail
        head = head.next
        
        for i in range(n - k % n - 1):
            head = head.next
        res = head.next
        head.next = None
        return res
```
