---
layout:     post
title:      LeetCode 622 Design Circular Queue (Python)
number:     622
level:      Medium
lcurl:      design-circular-queue
youtube:    Os1DC4S2j_E
bilibili1:  //player.bilibili.com/player.html?aid=417455960&bvid=BV1kV411n7Uk&cid=319898592&page=1
xigua:      
date:       2021-04-04
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Design
---

### 题目

Design your implementation of the circular queue. The circular queue is a linear data structure in which the operations are performed based on FIFO (First In First Out) principle and the last position is connected back to the first position to make a circle. It is also called "Ring Buffer".

One of the benefits of the circular queue is that we can make use of the spaces in front of the queue. In a normal queue, once the queue becomes full, we cannot insert the next element even if there is a space in front of the queue. But using the circular queue, we can use the space to store new values.

Implementation the MyCircularQueue class:

- MyCircularQueue(k) Initializes the object with the size of the queue to be k.
- int Front() Gets the front item from the queue. If the queue is empty, return -1.
- int Rear() Gets the last item from the queue. If the queue is empty, return -1.
- boolean enQueue(int value) Inserts an element into the circular queue. Return true if the operation is successful.
- boolean deQueue() Deletes an element from the circular queue. Return true if the operation is successful.
- boolean isEmpty() Checks whether the circular queue is empty or not.
- boolean isFull() Checks whether the circular queue is full or not.

### 解题思路

用一个长度为k的数组以及一个头指针进行模拟

### 代码
```python
class MyCircularQueue:

    def __init__(self, k: int):
        self.cap = k
        self.q = [0] * k
        self.ct = 0
        self.head = 0

    def enQueue(self, value: int) -> bool:
        if self.isFull():
            return False
        self.q[(self.head + self.ct) % self.cap] = value
        self.ct += 1
        return True

    def deQueue(self) -> bool:
        if self.isEmpty():
            return False
        self.head = (self.head + 1) % self.cap
        self.ct -= 1
        return True

    def Front(self) -> int:
        if not self.ct:
            return -1
        return self.q[self.head]

    def Rear(self) -> int:
        if not self.ct:
            return -1
        return self.q[(self.head + self.ct - 1) % self.cap]

    def isEmpty(self) -> bool:
        return self.ct == 0

    def isFull(self) -> bool:
        return self.ct == self.cap
```
