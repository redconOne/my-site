---
title: 'Isomorphic Strings'
date: 2023-01-11
draft: false
github_link: ''
author: 'Ming Lee Ng'
tags:
  - LeetCode 205
  - Hash Table
  - Strings
image: /images/blog/blog1.jpg
description: 'The Everyday Persons Guide to LeetCode #205'
toc:
socials:
---

## Introduction

Hello and welcome! I'm Ming Lee, and today we're going to cover **How to solve LeetCode 205 - Isomorphic Strings - in JS/TS :zap:**

Same as always we're gonna solve this, and we're gonna do it without the big fancy words because this is for regular folx! Keeping it nice and casual
round these parts! Movin' on...

## Problem

<b><a href='https://leetcode.com/problems/'>`LeetCode 205 - Isomorphic Strings`</a></b>

Given two strings s and t, determine if they are isomorphic.

Two strings s and t are isomorphic if the characters in s can be replaced to get t.

All occurrences of a character must be replaced with another character while preserving the order of characters. No two characters may map to the same
character, but a character may map to itself.

## Explanation

If you're anything like me you read that description and immediately had to return to the top for a second read. Basically we need to iterate through
the first string and map each character of str1[i] to str2[i]. But once the character has been mapped if we come across it again we need to ensure
that str2[i] is equal to the originally mapped character. If not, we return false. The funny part about this is that str1 can look isomorphic at
first, but we also have to compare str2 to str1, so be prepared to compare str1 to str2 and str2 to str1. If we make it through all the comparisons
without a hitch we can return true.

So the first thing we need to do is create something to hold our mapped values. Feel free to use a Map object or something, but in this case I'll be
tackling this with an key:value dictionary object.

Once your map/dictionary is set up we need to start our iteration. We need to iterate through every element of str1. If str[i] is in the dictionary we
need to verify that str2[i] === that dictionary value. If so, continue, if not, return false. In the event str[i] is not in the dictionary we just
need to add it to the dictionary.

Once we've iterated through the str1 comparison without returning false we need to do the same for str2 -> str1. Once that's all said and done if we
haven't returned false yet the only thing left to do is return true. Nice! Lets take a look at how all that looks in code!

## Solution

```
function isIsomorphic (str1: string, str2: string): boolean {
  let dict: { [key: string]: string } = {};

  for(const i in str1.split(''))
    if(!dict[str1[i]]) dict[str1[i]] = str2[i];
    else if(dict[str1[i]] !== str2[i]) return false;

  dict = {};

  for(const i in str2.split(''))
    if(!dict[str2[i]]) dict[str2[i]] = str1[i];
    else if(dict[str2[i]] !== str1[i]) return false;

  return true;
}
```

## Closing

Good work everyone! This one sound a lot more complicated than it actually is. Once you get the hang of it its one of those problems thats pretty fun
to do and quick to just blast right through. Our next problem is going to require a lot of thinking, so make sure you get a good night's rest before
we look at <a href='../reverselinkedlist/'>**`LeetCode 206 - Reverse Linked List`**</a>! See you then!
