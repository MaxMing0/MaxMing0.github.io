---
layout:     post
title:      LeetCode 237 Delete Node in a Linked List (Python)
number:     237
level:      Easy
lcurl:      delete-node-in-a-linked-list
youtube:    pcpQrFsI0eU
bilibili1:  //player.bilibili.com/player.html?aid=625976265&bvid=BV1vt4y1y7eM&cid=197883943&page=1
xigua:      
date:       2020-06-02
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Linked List
---

### 题目

Write a function to delete a node (except the tail) in a singly linked list, given only access to that node.

### 解题思路

使给的节点的值等于下一个节点的值，并删除下一个节点

### 代码
```python
class Solution:
    def deleteNode(self, node):
        """
        :type node: ListNode
        :rtype: void Do not return anything, modify node in-place instead.
        """
        node.val = node.next.val
        node.next = node.next.next
```
