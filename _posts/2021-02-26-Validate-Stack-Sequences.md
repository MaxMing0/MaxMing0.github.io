---
layout:     post
title:      LeetCode 946 Validate Stack Sequences (Python)
number:     946
level:      Medium
lcurl:      validate-stack-sequences
youtube:    A-UTZmNY2Q4
bilibili1:  //player.bilibili.com/player.html?aid=586990183&bvid=BV1fz4y1y7rS&cid=303510972&page=1
xigua:      
date:       2021-02-26
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Stack
---

### 题目

Given two sequences pushed and popped with distinct values, return true if and only if this could have been the result of a sequence of push and pop operations on an initially empty stack.

### 解题思路

按照pushed的顺序压栈，如果栈顶元素与popped的相同，则pop，最后判断是否所有元素都被pop完

### 代码
```python
class Solution:
    def validateStackSequences(self, pushed: List[int], popped: List[int]) -> bool:
        j, s, l = 0, [], len(popped)
        for x in pushed:
            s.append(x)
            while s and s[-1] == popped[j]:
                s.pop()
                j += 1
        return j == l
```
