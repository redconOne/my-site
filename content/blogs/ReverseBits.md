---
title: 'Reverse Bits'
date: 2023-01-07
draft: false
github_link: ''
author: 'Ming Lee Ng'
tags:
  - LeetCode 190
  - Divide and Conquer
  - Bit Manipulation
image: /images/blog/blog3.jpg
description: 'The Everyday Persons Guide to LeetCode #190'
toc:
socials:
---

## Introduction

Hello and welcome! I'm Ming Lee, and today we're going to cover **How to solve LeetCode 190 - Reverse Bits - in JS/TS :zap:**

Same as always we're gonna solve this, and we're gonna do it without the big fancy words because this is for regular folx! Keeping it nice and casual
round these parts! Movin' on...

## Problem

<b><a href='https://leetcode.com/problems/reverse-bits'>`LeetCode 190 - Reverse Bits`</a></b>

Reverse bits of a given 32 bits unsigned integer.

## Explanation

Ok, so there are some really fun and really fancy ways to approach this problem, but we're going to slow things down and take a nice and straight
forward approach. First of all, what the heck are they asking for? Well, they're giving us a number, and they want that number to be converted to
binary. From there all the 0's need to become 1's and all the 1's need to become 0's. One of the easiest ways to handle this, is to first convert the
number to binary with a simple toString(2).

From there we needto ensure that we're using a 32 bit integer, aka a binary number with 32 digits. We can handle that by padding the start of the
string up to a length of 32 with '0' using padStart('0')

After that we just need to split, reverse, join, and parse into a number and we're good to go!

## Solution

```
function reverseBits(n: number): number {
  const nStr = n.toString(2).padStart(32, '0');
  const nArr = nStr.split('').reverse();
  return parseInt(nArr.join(''), 2)
}
```

## Closing

This is a fast and fun one once you get the hang of what it's asking for. There's also something to be said for two's complement, which is stuff that
you can look in to, but be careful for negative numbers if you decide to head that route. Try playing around and see if you can make this into a
one-liner! It'll probably be kinda long and ugly looking, but it should definitely be do-able! We'll be dealing wiht some more binary type work in our
next problem - <a href='../numberof1bits/'>**`LeetCode 191 - Number of 1 Bits`**</a>! See you then!
