---
layout:     post
title:      LeetCode 1673 Find the Most Competitive Subsequence (Python)
number:     1673
level:      Medium
lcurl:      find-the-most-competitive-subsequence
youtube:    i3z1s5B_8cM
bilibili1:  //player.bilibili.com/player.html?aid=886373476&bvid=BV1yK4y1H7ni&cid=285420234&page=1
xigua:      
date:       2021-01-21
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Stack
    - Greedy
---

### 题目

Given an integer array nums and a positive integer k, return the most competitive subsequence of nums of size k.

An array's subsequence is a resulting sequence obtained by erasing some (possibly zero) elements from the array.

We define that a subsequence a is more competitive than a subsequence b (of the same length) if in the first position where a and b differ, subsequence a has a number less than the corresponding number in b. For example, [1,3,4] is more competitive than [1,3,5] because the first position they differ is at the final number, and 4 is less than 5.

### 解题思路

贪心，维护一个单调栈使得结果中的数是最小的，当剩余数的个数刚好能凑够k个的时候，就不能再pop了

### 代码
```python
class Solution:
    def mostCompetitive(self, nums: List[int], k: int) -> List[int]:
        stack = []
        for i, n in enumerate(nums):
            while stack and stack[-1] > n and i + k - len(stack) < len(nums):
                stack.pop()
            if len(stack) < k:
                stack.append(n)
        return stack
```
