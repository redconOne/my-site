---
title: 'Longest Common Prefix'
date: 2022-12-08
draft: false
github_link: ''
author: 'Ming Lee Ng'
tags:
  - LeetCode 14
  - Longest Common Prefix
  - Strings
image: /images/blog/blog1.jpg
description: 'The Everyday Persons Guide to LeetCode #14'
toc:
socials:
---

## Introduction

Hello and welcome! I'm Ming Lee, and today we're going to cover **How to solve
LeetCode 14 - Longest Common Prefix - in JS/TS :zap:**

Same as always we're gonna solve this, and we're gonna do it without the big
fancy words because this is for regular folx! Keeping it nice and casual round
these parts! Movin' on...

## Problem

<b><a href='https://leetcode.com/problems/longest-common-prefix'>`LeetCode 14 - Longest Common Prefix`</a></b>

Write a function to find the longest common prefix string amongst an array of
strings.

If there is no common prefix, return an empty string ''.

## Explanation

Sweet, so this sounds a little funky, but its a lot easier than it reads! So
basically, we're gonna get a whole bunch of strings in an array, and we need to
find the largest substring that they all start with in common! Now, lets look at
this example, ['flower', 'flow', 'flight']. We can handle this in a very clever
way by setting our prefix var to 'flower'. From there, we can check and see if
all the words .startWith(prefix), or rather, if they start with 'flower'. They
do not all start with flower, so we can adjust prefix to be a little smaller,
like 'flowe'. They do not all start with that either, so next we use 'flow' then
'flo', then finally 'fl', which they do all start with. We would then return
that value. If we continue all the way down to '', all of the strings will
contain at least that, so we will return prefix as ''.

## Solution

```
function longestCommonPrefix(strs: string[]): string {
    var prefix = strs[0];

    while(prefix.length > 0)
        if(strs.every((str) => str.startsWith(prefix))) return prefix;
        else prefix = prefix.slice(0, prefix.length - 1);

    return prefix;
}
```

## Closing

Alright! That code there should get us past the tests! This is one of those fun
ones that kind of tests how well you can work with strings. We're using slice,
which is a super common string method, .every(), which is super handy to have in
the toolbelt, and also startsWith, which we don't always get an opportunity to
use. Be careful when using slice(), as its really easy to get mixed up and end
up with an off-by-one error there! Other than that, this should be relatively
straight forward! Tomorrow we'll work on a fun problem and take a look at using
Stacks! Can't wait to take down
<a href='../validparenthesis/'>**`LeetCode 20 - Valid Parentheses`**</a>! See
you then!
