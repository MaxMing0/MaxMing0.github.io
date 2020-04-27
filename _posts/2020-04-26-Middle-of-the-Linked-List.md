---
layout:     post
title:      LeetCode 876 Middle of the Linked List (Python)
number:     876
level:      Easy
lcurl:      middle-of-the-linked-list
youtube:    804TcLDwp2w
bilibili1:  //player.bilibili.com/player.html?aid=455177043&bvid=BV1N5411t7Xm&cid=175574009&page=1
xigua:      
date:       2020-04-26
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Linked List
---

### 题目

Given a non-empty, singly linked list with head node head, return a middle node of linked list.

If there are two middle nodes, return the second middle node.

### 解题思路



### 代码
```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def middleNode(self, head: ListNode) -> ListNode:
        fast = slow = head
        while fast and fast.next:
            fast = fast.next.next
            slow = slow.next
        return slow
```