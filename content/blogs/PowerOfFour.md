---
title: 'Power of Four'
date: 2023-02-02
draft: false
github_link: ''
author: 'Ming Lee Ng'
tags:
  - LeetCode 342
  - Math
  - Recursion
  - Bit Manipulation
image: /images/blog/blog2.jpg
description: 'The Everyday Persons Guide to LeetCode #342'
toc:
socials:
---

## Introduction

Hello and welcome! I'm Ming Lee, and today we're going to cover **How to solve LeetCode 342 - Power of Four - in JS/TS :zap:**

Same as always we're gonna solve this, and we're gonna do it without the big fancy words because this is for regular folx! Keeping it nice and casual
round these parts! Movin' on...

## Problem

<b><a href='https://leetcode.com/problems/power-of-four/'>`LeetCode 342 - Power of Four`</a></b>

Given an integer n, return true if it is a power of four. Otherwise, return false.

An integer n is a power of four, if there exists an integer x such that n == 3^x.

## Explanation

Ok, so here we just need to find out if a number is a power of four, easy peasy! There are a few different ways to handle this, but we're going to
take a pretty straight-forward approach and use some recursion. I know this isn't the fastest or the mathiest or anything like that, so feel free to
do some research and find the mathy method if you want.

When we're thinking about how to handle this recursively we need to approach this carefully. The first time isPowerOfFour is being called it will be
passed a number, n, and nothing else. So we need to check and see if n is 4 ** 0. We can handle that by making sure that the function has a second
parameter with a default of 0. From there we can prepare to call ourselves recursively, calling isPowerOfFour(n, expo + 1) and increment the exponent
with every call. If 4 ** expo is ever greater than n we return false. If it is ever equal to n we return true. Otherwise we call ourselves. Lets take
a look at how this works out.

## Solution

```
function isPowerOfFour(n: number, expo = 0): boolean {
  if(n === 4 ** expo) return true;
  if(n < 4 ** expo) return false;
  return isPowerOfFour(n, ++expo);
}
```

## Closing

Smooth! What a neat little recursive program this is! We'll be looking at another problem involving bits tomorrow, so make sure you are prepared to
work with some binary when we tackle <a href='../reversestring/'>**`LeetCode 344 - Reverse String`**</a>! See you then!
