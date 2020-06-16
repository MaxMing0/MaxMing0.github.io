---
layout:     post
title:      LeetCode 468 Validate IP Address (Python)
number:     468
level:      Medium
lcurl:      validate-ip-address
youtube:    ZmSbFYB2nuM
bilibili1:  //player.bilibili.com/player.html?aid=838564663&bvid=BV1tg4y1q7Kq&cid=202607649&page=1
xigua:      
date:       2020-06-16
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - String
---

### 题目

Write a function to check whether an input string is a valid IPv4 address or IPv6 address or neither.

IPv4 addresses are canonically represented in dot-decimal notation, which consists of four decimal numbers, each ranging from 0 to 255, separated by dots ("."), e.g.,`172.16.254.1`;

Besides, leading zeros in the IPv4 is invalid. For example, the address `172.16.254.01` is invalid.

IPv6 addresses are represented as eight groups of four hexadecimal digits, each group representing 16 bits. The groups are separated by colons (":"). For example, the address `2001:0db8:85a3:0000:0000:8a2e:0370:7334` is a valid one. Also, we could omit some leading zeros among four hexadecimal digits and some low-case characters in the address to upper-case ones, so `2001:db8:85a3:0:0:8A2E:0370:7334` is also a valid IPv6 address(Omit leading zeros and using upper cases).

However, we don't replace a consecutive group of zero value with a single empty group using two consecutive colons (::) to pursue simplicity. For example, `2001:0db8:85a3::8A2E:0370:7334` is an invalid IPv6 address.

Besides, extra leading zeros in the IPv6 is also invalid. For example, the address `02001:0db8:85a3:0000:0000:8a2e:0370:7334` is invalid.

Note: You may assume there is no extra space or special characters in the input string.

### 解题思路

1. 数点或者冒号的个数进行分类，再分别按要求进行判断

### 代码
```python
class Solution:
    def validIPAddress(self, IP: str) -> str:
        pv4 = re.compile(r'^(([0-9]|[1-9][0-9]|1[0-9][0-9]|2[0-4][0-9]|25[0-5])\.){3}([0-9]|[1-9][0-9]|1[0-9][0-9]|2[0-4][0-9]|25[0-5])$')
        if pv4.match(IP):
            return "IPv4"
        pv6 = re.compile(r'^(([0-9a-f]{1,4}):){7}([0-9a-f]{1,4})$')
        if pv6.match(IP.lower()):
            return "IPv6"
        return "Neither"
```

```python
class Solution:
    def validIPAddress(self, IP: str) -> str:
        def isIPv4(IP):
            ip = IP.split('.')
            for s in ip:
                if len(s) == 0 or len(s) > 3:
                    return 'Neither'
                if ((s[0] == '0' and len(s) != 1) or not s.isdigit() or int(s) > 255):
                    return 'Neither'
            return 'IPv4'

        def isIPv6(IP: str) -> str:
            ip = IP.split(':') 
            for s in ip:
                if len(s) == 0 or len(s) > 4:
                    return "Neither"
                for c in s:
                     if c not in '0123456789abcdef':
                        return "Neither"
            return 'IPv6'

        if len(IP.split('.'))-1 == 3:
            return isIPv4(IP)
        elif len(IP.split(':'))-1 == 7:
            return isIPv6(IP.lower())
        return "Neither"
```
