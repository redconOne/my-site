---
title: 'Add Digits'
date: 2023-01-23
draft: false
github_link: ''
author: 'Ming Lee Ng'
tags:
  - LeetCode 258
  - Math
  - Simulation
  - Number Theory
image: /images/blog/blog1.jpg
description: 'The Everyday Persons Guide to LeetCode #258'
toc:
socials:
---

## Introduction

Hello and welcome! I'm Ming Lee, and today we're going to cover **How to solve LeetCode 258 - Add Digits - in JS/TS :zap:**

Same as always we're gonna solve this, and we're gonna do it without the big fancy words because this is for regular folx! Keeping it nice and casual
round these parts! Movin' on...

## Problem

<b><a href='https://leetcode.com/problems/add-digits/'>`LeetCode 258 - Add Digits`</a></b>

Given an integer num, repeatedly add all its digits until the result has only one digits, and return it.

## Explanation

Ok, so this is a fun one. We just need to keep summing those digits until the result has only one digit? Ezpz. The first thing we need to do is
establish a base case. If the number in question only has one digit it must be less than 10. So if the number is less than 10 we return num.

If the number is greater than 10 we need to look at each digit individually, so lets convert it to a string first, then an array, then use reduce to
sum all those digits.

But after we sum all the digits and get our number we would need to check if that is viable to return. Which we already did once in our base case. So
this is a good point to start recursively calling ourselves. We can take the summed digits and slap them into another addDigits() call. All in all
things should look a little like the following:

## Solution

```
function addDigits(num: number): number {
  if(num < 10) return num;

  return addDigits(num.toString().split('').reduce((sum, x) => sum + +x, 0));
}
```

## Closing

Nice! Keep those recursive/mathy thoughts going because we'll need them in our next one,
<a href='../uglynumber/'>**`LeetCode 263 - Ugly Number`**</a>! See you then!
