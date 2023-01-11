---
title: 'Number of 1 Bits'
date: 2023-01-08
draft: false
github_link: ''
author: 'Ming Lee Ng'
tags:
  - LeetCode 191
  - Divide and Conquer
  - Bit Manipulation
image: /images/blog/blog1.jpg
description: 'The Everyday Persons Guide to LeetCode #191'
toc:
socials:
---

## Introduction

Hello and welcome! I'm Ming Lee, and today we're going to cover **How to solve LeetCode 191 - Number of 1 Bits - in JS/TS :zap:**

Same as always we're gonna solve this, and we're gonna do it without the big fancy words because this is for regular folx! Keeping it nice and casual
round these parts! Movin' on...

## Problem

<b><a href='https://leetcode.com/problems/number-of-1-bits'>`LeetCode 191 - Number of 1 Bits`</a></b>

Write a function that takes an unsigned integer and returns the number of '1' bits it has (also known as the Hamming weight).

## Explanation

Ok this is another problem that can be solved with a fairly straight-forward approach. All the problem is asking for is for you to turn a number into
binary, and then return the number of '1's within that particular binary number.

So the first thing we need to do is convert the decimal number to binary. We can handle that with toString(2).

From there we need to remove all the '0's. We can either split that into an array and filter, or do a replace. I'll do a replace(/0/g, '')

After we've removed all the 0's all we have left in the string are the 1's that are being used in that binary number. So we just return the .length of
that string and we're done! Easy peasy! It should look a little like the following.

## Solution

```
function hammingWeight(n: number): number {
  return n.toString(2).replace(/0/g, '').length;
}
```

## Closing

Nice! This one was fun, and we ended up with a cool one-liner! Get ready to continue playing with numbers for tomorrow's problem
<a href='../happynumber/'>**`LeetCode 202 - Happy Number`**</a>! See you then!
