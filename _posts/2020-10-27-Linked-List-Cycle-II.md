---
layout:     post
title:      LeetCode 142 Linked List Cycle II (Python)
number:     142
level:      Medium
lcurl:      linked-list-cycle-ii
youtube:    fh5JNl62H7Q
bilibili1:  //player.bilibili.com/player.html?aid=457583609&bvid=BV1W5411L7AF&cid=250014514&page=1
xigua:      
date:       2020-10-27
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Linked List
---

### 题目

Given a linked list, return the node where the cycle begins. If there is no cycle, return null.

There is a cycle in a linked list if there is some node in the list that can be reached again by continuously following the next pointer. Internally, pos is used to denote the index of the node that tail's next pointer is connected to. Note that pos is not passed as a parameter.

Notice that you should not modify the linked list.

Follow up:

Can you solve it using O(1) (i.e. constant) memory?

### 解题思路

使用快慢指针，设链表起点到环起点的距离为a，环起点距快慢指针相遇点距离为b，相遇点距环起点距离为c

`a + (n + 1)b + nc = 2(a + b)` => `a = c + (n - 1)(b + c)`

两个指针，从链表起点和快慢指针相遇点，每次移动一个，会在环起点相遇

### 代码
```python
class Solution:
    def detectCycle(self, head: ListNode) -> ListNode:
        slow = fast = head
        while fast and fast.next:
            fast = fast.next.next
            slow = slow.next
            if fast == slow:
                slow2 = head
                while slow != slow2:
                    slow = slow.next
                    slow2 = slow2.next
                return slow
        return None
```
