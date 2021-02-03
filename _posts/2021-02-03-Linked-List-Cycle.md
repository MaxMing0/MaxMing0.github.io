---
layout:     post
title:      LeetCode 141 Linked List Cycle (Python)
number:     141
level:      Easy
lcurl:      linked-list-cycle
youtube:    2PBLfCMpq3I
bilibili1:  //player.bilibili.com/player.html?aid=714092209&bvid=BV1KX4y157vh&cid=292343947&page=1
xigua:      
date:       2021-02-03
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Linked List
---

### 题目

Given head, the head of a linked list, determine if the linked list has a cycle in it.

There is a cycle in a linked list if there is some node in the list that can be reached again by continuously following the next pointer. Internally, pos is used to denote the index of the node that tail's next pointer is connected to. Note that pos is not passed as a parameter.

Return true if there is a cycle in the linked list. Otherwise, return false.

### 解题思路

使用快慢指针，如果可以相遇，则是存在环

### 代码
```python
class Solution:
    def hasCycle(self, head: ListNode) -> bool:
        fast = slow = head
        while fast and fast.next:
            fast = fast.next.next
            slow = slow.next
            if slow == fast:
                return True
        return False
```
