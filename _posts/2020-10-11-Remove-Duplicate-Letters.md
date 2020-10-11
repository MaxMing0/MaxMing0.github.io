---
layout:     post
title:      LeetCode 316 Remove Duplicate Letters (Python)
number:     316
level:      Medium
lcurl:      remove-duplicate-letters
youtube:    2MNOHSxE-Yc
bilibili1:  //player.bilibili.com/player.html?aid=839924224&bvid=BV1x54y1R7y7&cid=244761783&page=1
xigua:      
date:       2020-10-11
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Greedy
    - Stack
---

### 题目

Given a string s, remove duplicate letters so that every letter appears once and only once. You must make sure your result is the smallest in lexicographical order among all possible results.

Note: This question is the same as 1081: https://leetcode.com/problems/smallest-subsequence-of-distinct-characters/

### 解题思路

贪心，结果维护在一个单调栈中，在pop时候考试一个字符串能否被删，如果不是最后一次出现才可以被删，已经出现过的字符就不加到栈中

### 代码
```python
class Solution:
    def removeDuplicateLetters(self, s) -> int:
        stack = []
        seen = set()
        last = {c: i for i, c in enumerate(s)}
        for i, c in enumerate(s):
            if c not in seen:
                while stack and c < stack[-1] and i < last[stack[-1]]:
                    seen.remove(stack.pop())
                seen.add(c)
                stack.append(c)
        return ''.join(stack)
```
