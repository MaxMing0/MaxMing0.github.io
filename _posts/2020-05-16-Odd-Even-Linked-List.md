---
layout:     post
title:      LeetCode 328 Odd Even Linked List (Python)
number:     328
level:      Medium
lcurl:      odd-even-linked-list
youtube:    lk-6nRW5hnU
bilibili1:  //player.bilibili.com/player.html?aid=838215431&bvid=BV1ag4y1B78z&cid=191679254&page=1
xigua:      
date:       2020-05-16
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Linked List
---

### 题目

Given a singly linked list, group all odd nodes together followed by the even nodes. Please note here we are talking about the node number and not the value in the nodes.

You should try to do it in place. The program should run in O(1) space complexity and O(nodes) time complexity.

- The relative order inside both the even and odd groups should remain as it was in the input.
- The first node is considered odd, the second node even and so on ...

### 解题思路

把所有奇数位置的节点连到一起，偶数位置的节点连到一起，最后把奇数的最后一个节点指向偶数的头。

### 代码
```python
class Solution:
    def oddEvenList(self, head: ListNode) -> ListNode:
        if not head:
            return head
        odd, even, even_head = head, head.next, head.next
        while even and even.next:
            odd.next = even.next
            odd = odd.next
            even.next = odd.next
            even = even.next
        odd.next = even_head
        return head
```
