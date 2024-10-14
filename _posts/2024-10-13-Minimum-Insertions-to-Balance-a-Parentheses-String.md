---
layout:     post
title:      LeetCode 1541 Minimum Insertions to Balance a Parentheses String (Python)
number:     1541
level:      Medium
lcurl:      minimum-add-to-make-parentheses-valid
youtube:    
bilibili1:  
xigua:      
date:       2024-10-13
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - 
---

### 题目

Given a parentheses string s containing only the characters '(' and ')'. A parentheses string is balanced if:

Any left parenthesis '(' must have a corresponding two consecutive right parenthesis '))'.
Left parenthesis '(' must go before the corresponding two consecutive right parenthesis '))'.
In other words, we treat '(' as an opening parenthesis and '))' as a closing parenthesis.

For example, "())", "())(())))" and "(())())))" are balanced, ")()", "()))" and "(()))" are not balanced.
You can insert the characters '(' and ')' at any position of the string to balance it if needed.

Return the minimum number of insertions needed to make s balanced.

### 解题思路

维护两个变量，一个是已经增加的左右括号个数`res`，一个是还需要多少右括号`right`

如果是`)`,`right-1`,如果`right`小于0了，则需要增加一个左括号，并需要两个右括号

如果是`(`,如果现在需要奇数个右括号，则增加一个右括号和左括号匹配

### 代码
```python
class Solution:
    def minInsertions(self, s: str) -> int:
        res = right = 0
        for c in s:
            if c == "(":
                if right % 2:
                    right -= 1
                    res += 1
                right += 2
            else:
                right -= 1
                if right < 0:
                    right += 2
                    res += 1
        return res + right
```
