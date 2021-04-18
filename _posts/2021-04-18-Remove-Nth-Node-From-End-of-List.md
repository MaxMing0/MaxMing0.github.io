---
layout:     post
title:      LeetCode 19 Remove Nth Node From End of List (Python)
number:     19
level:      Medium
lcurl:      remove-all-adjacent-duplicates-in-string-ii
youtube:    oFwuLUU8dHM
bilibili1:  //player.bilibili.com/player.html?aid=460208384&bvid=BV1Z5411c79y&cid=325950687&page=1
xigua:      
date:       2021-04-18
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Linked List
---

### 题目

Given the head of a linked list, remove the nth node from the end of the list and return its head.

Follow up: Could you do this in one pass?

### 解题思路

使用两个指针，第一先移动n次，然后同时移动，找到倒数第n个节点，然后删除

### 代码
```python
class Solution:
    def removeNthFromEnd(self, head: ListNode, n: int) -> ListNode:
        first = ListNode(0)
        second = ListNode(0)
        first.next = head
        second.next = head
        for i in range(n):
            first = first.next
        if first.next == None:
            return head.next
        while first.next != None:
            first = first.next
            second = second.next
        second.next = second.next.next
        return head
```
