---
layout:     post
title:      LeetCode 143 Reorder List (Python)
number:     143
level:      Medium
lcurl:      reorder-list
youtube:    QTqlIGvRZyI
bilibili1:  //player.bilibili.com/player.html?aid=286787552&bvid=BV1Jf4y1Q7y7&cid=226695796&page=1
xigua:      
date:       2020-08-20
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Linked List
---

### 题目

Given a singly linked list L: L0→L1→…→Ln-1→Ln,
reorder it to: L0→Ln→L1→Ln-1→L2→Ln-2→…

You may not modify the values in the list's nodes, only nodes itself may be changed.

### 解题思路

首先使用快慢指针，将链表分成两段，然后将第二段翻转，最后将两个链表相交形成最后的结果

### 代码
```python
class Solution:
    def reorderList(self, head: ListNode) -> None:
        if not head or not head.next or not head.next.next:
            return
        slow, fast = head, head
        while fast.next and fast.next.next:
            slow = slow.next
            fast = fast.next.next
        head2 = slow.next
        slow.next = None
        dummy = ListNode(0, None)
        while head2:
            tmp = head2.next
            head2.next = dummy.next
            dummy.next = head2
            head2 = tmp
        head1 = head
        head2 = dummy.next
        while head1 and head2:
            tmp = head2
            head2 = head2.next
            tmp.next = head1.next
            head1.next = tmp
            head1 = head1.next.next
```
