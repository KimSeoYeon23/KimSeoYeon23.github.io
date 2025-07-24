---
layout: post
title:  "Palindrome Number"
date:   2025-07-22 09:25:00 +0900
categories:
  - Dev
  - codingtest
tag: codingtest
comments: true
---

* this unordered seed list will be replaced by the toc
{:toc}

## LeetCode Palindrome Number

### 문제

Given an integer x, return true if x is a palindrome, and false otherwise.


### 예시

Example 1:

Input: x = 121
Output: true
Explanation: 121 reads as 121 from left to right and from right to left.
Example 2:

Input: x = -121
Output: false
Explanation: From left to right, it reads -121. From right to left, it becomes 121-. Therefore it is not a palindrome.
Example 3:

Input: x = 10
Output: false
Explanation: Reads 01 from right to left. Therefore it is not a palindrome.

## 풀이

```py
class Solution:
  def isPalindrome(self, x: int) -> bool:
    return True if str(x)[::-1] == str(x) else False
```
