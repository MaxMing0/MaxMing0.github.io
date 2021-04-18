---
layout:     post
title:      LeetCode 1209 Remove All Adjacent Duplicates in String II (Python)
number:     1209
level:      Hard
lcurl:      remove-all-adjacent-duplicates-in-string-ii
youtube:    D6KKjqeQWTs
bilibili1:  //player.bilibili.com/player.html?aid=332654259&bvid=BV1qA411L7z9&cid=325926551&page=1
xigua:      
date:       2021-04-18
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Stack
---

### 题目

You are given a string s and an integer k, a k duplicate removal consists of choosing k adjacent and equal letters from s and removing them, causing the left and the right side of the deleted substring to concatenate together.

We repeatedly make k duplicate removals on s until we no longer can.

Return the final string after all such duplicate removals have been made. It is guaranteed that the answer is unique.

### 解题思路

使用栈，栈里元素为当前字母连续出现了几次，到k次就pop

### 代码
```python
class Solution:
    def removeDuplicates(self, s: str, k: int) -> str:
        stack = [['#', 0]]
        for c in s:
            if c == stack[-1][0]:
                stack[-1][1] += 1
                if stack[-1][1] == k:
                    stack.pop()
            else:
                stack.append([c, 1])
        return ''.join([c[0] * c[1] for c in stack[1:]])
```
