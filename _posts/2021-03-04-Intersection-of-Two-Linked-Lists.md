---
layout:     post
title:      LeetCode 160 Intersection of Two Linked Lists (Python)
number:     160
level:      Easy
lcurl:      intersection-of-two-linked-lists
youtube:    Dk2-0A8soHw
bilibili1:  //player.bilibili.com/player.html?aid=886983810&bvid=BV18K4y1J7wx&cid=306137690&page=1
xigua:      
date:       2021-03-04
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Linked List
---

### 题目

Write a program to find the node at which the intersection of two singly linked lists begins.

### 解题思路

两个指针同时遍历两个链表，当到达一个尾骨之后，换到另一的头部继续遍历，两个指针会在链表的相交节点相遇

### 代码
```python
class Solution:
    def getIntersectionNode(self, headA: ListNode, headB: ListNode) -> ListNode:
        if not headA or not headB:
            return None
        pa, pb = headA, headB
        while pa is not pb:
            pa = headB if pa is None else pa.next
            pb = headA if pb is None else pb.next
        return pa
``` 
