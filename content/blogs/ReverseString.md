---
title: 'Reverse String'
date: 2023-02-03
draft: false
github_link: ''
author: 'Ming Lee Ng'
tags:
  - LeetCode 344
  - Strings
  - Two Pointers
image: /images/blog/blog3.jpg
description: 'The Everyday Persons Guide to LeetCode #344'
toc:
socials:
---

## Introduction

Hello and welcome! I'm Ming Lee, and today we're going to cover **How to solve LeetCode 344 - Reverse String - in JS/TS :zap:**

Same as always we're gonna solve this, and we're gonna do it without the big fancy words because this is for regular folx! Keeping it nice and casual
round these parts! Movin' on...

## Problem

<b><a href='https://leetcode.com/problems/reverse-string/'>`LeetCode 344 - Reverse String`</a></b>

Write a function that reverses a string. The input string is given as an array of characters s.

You must do this by modifying the input array in-place with O(1) extra memory.

## Explanation

Ok, so we just need to reverse a string, but we need it mutated, not a completely new string. That sounds do-able.

So because we don't need to return anything and because we're mutating the string passed in as an argument we know that we won't need to declare any
variables, so let's get right to the for loop.

We want to iterate over half of the characters (to swap them out with the back half) so we can start our for loop at 0 and continue as long as i is
less than half of s.length.

Once we're in the for loop we need to swap s[i] with s[s.length - 1 - i]. We can do that pretty easily by just creating a new temporary variable. All
in all the solution should look a little like the following:

## Solution

```
function reverseString(s: string[]): void {
  for(let i = 0; i < s.length / 2; ++i){
    const temp = s[i];
    s[i] = s[s.length - 1 - i];
    s[s.length - 1 - i] = temp;
  }
}
```

## Closing

Nice! That one was pretty straight forward, and shouldn't have been too difficult. We'll be looking at a fairly similar problem tomorrow in
<a href='../reversevowelsofastring/'>**`LeetCode 345 - Reverse Vowels Of A String`**</a>! See you then!
