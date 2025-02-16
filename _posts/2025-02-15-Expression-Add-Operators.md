---
layout:     post
title:      LeetCode 282 Expression Add Operators (Python)
number:     282
level:      Hard
lcurl:      expression-add-operators
youtube:    
bilibili1:  
xigua:      
date:       2025-02-15
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - backtracking
---

### 题目

Given a string num that contains only digits and an integer target, return all possibilities to insert the binary operators '+', '-', and/or '*' between the digits of num so that the resultant expression evaluates to the target value.

Note that operands in the returned expressions should not contain leading zeros.

### 解题思路



### 代码
```python
class Solution:
    def addOperators(self, num: str, target: int) -> List[str]:
        def dfs(num, tmp, cur, last):
            if not num and cur == target:
                res.append(tmp)
                return
            for i in range(1, len(num) + 1):
                val = num[:i]
                if i == 1 or (i > 1 and num[0] != "0"):
                    dfs(num[i:], tmp + "+" + val, cur + int(val), int(val))
                    dfs(num[i:], tmp + "-" + val, cur - int(val), -int(val))
                    dfs(num[i:], tmp + "*" + val, cur - last + last * int(val), last * int(val))

        res = []
        for i in range(1, len(num) + 1):
            if i == 1 or (i > 1 and num[0] != "0"):
                dfs(num[i:], num[:i], int(num[:i]), int(num[:i]))
        return res
```
