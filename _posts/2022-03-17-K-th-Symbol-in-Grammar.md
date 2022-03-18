---
layout:     post
title:      LeetCode 779 K-th Symbol in Grammar (Python)
number:     779
level:      Medium
lcurl:      k-th-symbol-in-grammar
youtube:    xjtgtUP34pg
bilibili1:  
xigua:      
date:       2022-03-17
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - Recursive
---

### 题目

We build a table of n rows (1-indexed). We start by writing 0 in the 1st row. Now in every subsequent row, we look at the previous row and replace each occurrence of 0 with 01, and each occurrence of 1 with 10.

For example, for n = 3, the 1st row is 0, the 2nd row is 01, and the 3rd row is 0110.
Given two integer n and k, return the kth (1-indexed) symbol in the nth row of a table of n rows.

### 解题思路
```
k = k - 1
f(n,k) = f(n-1,k/2) if n % 2 == 0
         1 - f(n-1, k/2)     else
```
### 代码
```python
class Solution:
    def kthGrammar(self, n: int, k: int) -> int:
        def f(n, k):
            if n == 1:
                return 0
            return f(n - 1, k // 2) if k % 2 == 0 else 1 - f(n - 1, k // 2)
        k -= 1
        return f(n, k)
```
