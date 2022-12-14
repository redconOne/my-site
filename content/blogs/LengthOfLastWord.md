---
title: 'Length of Last Word'
date: 2022-12-14
draft: false
github_link: ''
author: 'Ming Lee Ng'
tags:
  - LeetCode 58
  - Length of Last Word
  - Strings
image: /images/blog/blog1.jpg
description: 'The Everyday Persons Guide to LeetCode #58'
toc:
socials:
---

## Introduction

Hello and welcome! I'm Ming Lee, and today we're going to cover **How to solve
LeetCode 58 - Length of Last Word - in JS/TS :zap:**

Same as always we're gonna solve this, and we're gonna do it without the big
fancy words because this is for regular folx! Keeping it nice and casual round
these parts! Movin' on...

## Problem

<b><a href='https://leetcode.com/problems/length-of-last-word'>`LeetCode 58 - Length of Last Word`</a></b>

Given a string s consisting of words and spaces, return the length of the last
word in the string.

A word is a maximal substring consisting of non-space characters only.

## Explanation

Sweet! This one should be super fun to handle. So we know that we're being given
a string of 'words' and we need to return the length of the last word in the
string. Now typically that just means that we need to split that string by ' ',
but there is another condition that we need to handle. Another part of the
instructions state that the maximal substring will consist of non-space
characters only. This is important as there **are** some situations where
splitting by ' ' will cause the final 'word' to be an empty segment like this
''. The cause for such an event is a string like the following => " lots of long
words here " This will split, but the elements in our split array will not be
"here", but rather "". To account for this we could either trim() the string in
advance or filter out the unwanted elements after the split. The choice is
programmer's preference here. I chose to do a trim(), so the code will look a
little something like this :

## Solution

```
function lengthOfLastWord(str: string): number {
    return str.trim().split(' ').reverse()[0].length;
}
```

## Closing

Perfect! This is a great problem for keeping up to snuff on your String methods,
and is a really fun one to solve as well! In this particular example I chose to
reverse so I can easily access the first element of the array, but that's
totally not necessary. One could just as easily access the final element of the
array by using .length - 1, but I took the lazy route! The next problem is gonna
be some addition fun, so everyone make sure and think mathy thoughts as we dive
into <a href='../plusone/'>**`LeetCode 66 - Plus One`**</a>! See you then!
