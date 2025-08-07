---
layout: post
title:  "Length of Last Word"
date:   2025-08-07 19:57:00 +0900
categories:
  - Dev
  - codingtest
tag: codingtest
comments: true
---

* this unordered seed list will be replaced by the toc
{:toc}

## LeetCode Length of Last Word

### 문제

Given a string s consisting of words and spaces, return the length of the last word in the string.

A word is a maximal substring consisting of non-space characters only.


### 예시

Example 1:

Input: s = "Hello World"
Output: 5
Explanation: The last word is "World" with length 5.

Example 2:
Input: s = "   fly me   to   the moon  "
Output: 4
Explanation: The last word is "moon" with length 4.

Example 3:
Input: s = "luffy is still joyboy"
Output: 6
Explanation: The last word is "joyboy" with length 6.


## 풀이

```py
class Solution:
    def lengthOfLastWord(self, s: str) -> int:
        split_str = list(s.split(" "))
        none_space = ' '.join(split_str).split()
        last_str = none_space[-1]
        return len(''.join(last_str))
        
```
