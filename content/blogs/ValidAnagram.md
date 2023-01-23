---
title: 'Valid Anagram'
date: 2023-01-21
draft: false
github_link: ''
author: 'Ming Lee Ng'
tags:
  - LeetCode 242
  - Hash Table
  - String
  - Sorting
image: /images/blog/blog2.jpg
description: 'The Everyday Persons Guide to LeetCode #242'
toc:
socials:
---

## Introduction

Hello and welcome! I'm Ming Lee, and today we're going to cover **How to solve LeetCode 242 - Valid Anagram - in JS/TS :zap:**

Same as always we're gonna solve this, and we're gonna do it without the big fancy words because this is for regular folx! Keeping it nice and casual
round these parts! Movin' on...

## Problem

<b><a href='https://leetcode.com/problems/valid-anagram'>`LeetCode 242 - Valid Anagram`</a></b>

Given two strings s and t, return true if t is an anagram of s, and false otherwise.

An Anagram is a word or phrase formed by rearranging the letters of a different word or phrase, typically using all the original letters exactly once.

## Explanation

Ok, so we just need to make sure that str1 and str2 both contain the same amount of the same letters. There are a few fun ways to handle this, but
lets try a fun one that shows off our knowledge of some fun functions.

So since we know these strings are supposed to contain the same number of each character we can always sort the strings alphabetically and then
compare and verify that the strings are identical. If so, they're anagrams, if not, return false! This one should be pretty easy to implement, so lets
look at the code.

## Solution

```
function isAnagram(str1: string, str2: string): boolean {
  str1 = str1.split('').sort().join('');
  str2 = str2.split('').sort().join('');
  return str1 === str2.
}
```

## Closing

Great work! This should have felt pretty easy. There are a lot of other ways to solve this, including using a hashmap, or using replace. There is
going to be some give/take in different implementations like a difference in time complexity or difficulty to code. Consider taking some time to try
and figure out some other ways to approach this and which one you prefer and why. Tomorrow's problem is going to be a fun one when we look at
<a href='../binarytreepaths/'>**`LeetCode 257 - Binary Tree paths`**</a>! See you then!
