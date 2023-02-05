---
title: 'Reverse Vowels of a String'
date: 2023-02-04
draft: false
github_link: ''
author: 'Ming Lee Ng'
tags:
  - LeetCode 345
  - Strings
  - Two Pointers
image: /images/blog/blog1.jpg
description: 'The Everyday Persons Guide to LeetCode #345'
toc:
socials:
---

## Introduction

Hello and welcome! I'm Ming Lee, and today we're going to cover **How to solve LeetCode 345 - Reverse Vowels of a String - in JS/TS :zap:**

Same as always we're gonna solve this, and we're gonna do it without the big fancy words because this is for regular folx! Keeping it nice and casual
round these parts! Movin' on...

## Problem

<b><a href='https://leetcode.com/problems/reverse-vowels-of-a-string/'>`LeetCode 345 - Reverse Vowels of a String`</a></b>

Given a string s, reverse only all the vowels in the string and return it.

The vowels are 'a' 'e' 'i' 'o' and 'u', and they can appear in both lower and upper cases, more than once.

## Explanation

Ok, so this one is pretty easy to understand the problem, but actual execution could get a little tricky. We need to iterate through a string,
replacing all the first vowels with the last ones. Probably one of the easiest ways to handle this is by iterating over the string once to find all
the vowels and push them into a stack (LIFO). When we do a second iteration we can replace those any vowel we come across with the next vowel on the
stack.

## Solution

```
function reverseVowels(s: string): string {
  const vowels = 'aeiouAEIOU';
  const stack: string[] = [];
  let result = '';

  for(const char of s)
    if(vowels.includes(char)) stack.push(char);

  for(const char of s)
    result += vowels.includes(char) ? stack.pop() : char;

  return result;
}
```

## Closing

Nicely done! That was a pretty fun one to solve! Tomorrow we'll be workin on
<a href='../intersectionoftwoarrays/'>**`LeetCode 349 - Intersection of Two Arrays`**</a>! See you then!
