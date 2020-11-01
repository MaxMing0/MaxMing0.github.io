---
layout:     post
title:      LeetCode 1290 Convert Binary Number in a Linked List to Integer (Python)
number:     1290
level:      Easy
lcurl:      convert-binary-number-in-a-linked-list-to-integer
youtube:    DSHzdj_DuS4
bilibili1:  //player.bilibili.com/player.html?aid=712741674&bvid=BV1nD4y1R7QH&cid=251573897&page=1
xigua:      
date:       2020-11-01
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Bit Manipulation
---

### 题目

Given head which is a reference node to a singly-linked list. The value of each node in the linked list is either 0 or 1. The linked list holds the binary representation of a number.

Return the decimal value of the number in the linked list.

### 解题思路

让结果等于头的数字，遍历链表，每次先将结果左移一位，然后与下一个链表中的数进行或运算

### 代码
```python
class Solution:
    def getDecimalValue(self, head: ListNode) -> int:
        num = head.val
        while head.next:
            num = (num << 1) | head.next.val
            head = head.next
        return num
```
