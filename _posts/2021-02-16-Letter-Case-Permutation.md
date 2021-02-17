---
layout:     post
title:      LeetCode 784 Letter Case Permutation (Python)
number:     784
level:      Medium
lcurl:      letter-case-permutation
youtube:    vjagg2armrI
bilibili1:  //player.bilibili.com/player.html?aid=246715730&bvid=BV1Sv411a7Gx&cid=298761606&page=1
xigua:      
date:       2021-02-16
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - 
---

### 题目

Given a string S, we can transform every letter individually to be lowercase or uppercase to create another string.

Return a list of all possible strings we could create. You can return the output in any order.

### 解题思路

从空字符串开始拓展，遍历输入字符串，如果当前字符是字母，则将现在所有的字符串拓展成大小写两个，否则将当前字符添加在后面

### 代码
```python
class Solution:
    def letterCasePermutation(self, S: str) -> List[str]:
        res = ['']
        for c in S:
            if c.isalpha():
                res = [i + j for i in res for j in [c.upper(), c.lower()]]
            else:
                res = [i + c for i in res]
        return res
```
