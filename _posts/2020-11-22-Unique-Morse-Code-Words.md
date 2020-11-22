---
layout:     post
title:      LeetCode 804 Unique Morse Code Words (Python)
number:     804
level:      Easy
lcurl:      unique-morse-code-words
youtube:    gcorFC0hmDc
bilibili1:  //player.bilibili.com/player.html?aid=712823985&bvid=BV1RD4y1Q7AM&cid=258554265&page=1
xigua:      
date:       2020-11-22
author:     小明MaxMing
header-img: img/post-bg-coffee.jpeg
catalog: false
tags:
    - 
---

### 题目

International Morse Code defines a standard encoding where each letter is mapped to a series of dots and dashes, as follows: "a" maps to ".-", "b" maps to "-...", "c" maps to "-.-.", and so on.

For convenience, the full table for the 26 letters of the English alphabet is given below:

```[".-","-...","-.-.","-..",".","..-.","--.","....","..",".---","-.-",".-..","--","-.","---",".--.","--.-",".-.","...","-","..-","...-",".--","-..-","-.--","--.."]```
Now, given a list of words, each word can be written as a concatenation of the Morse code of each letter. For example, "cab" can be written as "-.-..--...", (which is the concatenation "-.-." + ".-" + "-..."). We'll call such a concatenation, the transformation of a word.

Return the number of different transformations among all words we have.

### 解题思路

将字符串转换成morse code，然后放到一个set中，返回长度

### 代码
```python
class Solution:
    def uniqueMorseRepresentations(self, words: List[str]) -> int:
        morse = [".-","-...","-.-.","-..",".","..-.","--.","....","..",".---","-.-",".-..","--","-.","---",".--.","--.-",".-.","...","-","..-","...-",".--","-..-","-.--","--.."]
        translate = {''.join([morse[ord(c)-97] for c in word]) for word in words}
        return len(translate)
```
