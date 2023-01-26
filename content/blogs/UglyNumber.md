---
title: 'Ugly Number'
date: 2023-01-24
draft: false
github_link: ''
author: 'Ming Lee Ng'
tags:
  - LeetCode 263
  - Math
image: /images/blog/blog2.jpg
description: 'The Everyday Persons Guide to LeetCode #263'
toc:
socials:
---

## Introduction

Hello and welcome! I'm Ming Lee, and today we're going to cover **How to solve LeetCode 263 - Ugly Number - in JS/TS :zap:**

Same as always we're gonna solve this, and we're gonna do it without the big fancy words because this is for regular folx! Keeping it nice and casual
round these parts! Movin' on...

## Problem

<b><a href='https://leetcode.com/problems/ugly-number/'>`LeetCode 263 - Ugly Number`</a></b>

An ugly number is a positive integer whose prime factors are limited to 2, 3, and 5.

Given an integer n, return true if n is an ugly number.

## Explanation

Ok, so we need to return true if a number meets a certain specific set of conditions.

One of the first conditions mentioned is that it must be a positive number. So we know that if the number is negative we need to return false. The
number 0 also falls in this category, so let's return everything less than 0 as false.

If we make it past that case case we need to reduce it by dividing the number by either 2,3, or 5 until it is no longer divisible by any of those
three numbers. If n is 1 at this point, return true. If n is something other than 1 return false. Lets take a look at the recursion that we're going
to consider for this.

So lets first check to see if n is divisible by 2. If so, we divide it by two and recursively call ourselves.

```
if (!n%2) return isUgly(n / 2);
```

We need to do the same for numbers 3 and 5. After it makes it through all those if statements we return n === 1. Lets take a look at this in code.

## Solution

```
function isUgly(n: number): boolean {
  if(n <= 0) return false;
  if(!(n % 2)) return isUgly(n / 2);
  if(!(n % 3)) return isUgly(n / 3);
  if(!(n % 5)) return isUgly(n / 5);
  return n === 1;
}
```

## Closing

Nice! That was a funky one to get the hang of, but just keep at it and it'll make more sense. Next we'll be taking a look at
<a href='../missingnumber/'>**`LeetCode 268 - Missing Number`**</a>! See you then!
