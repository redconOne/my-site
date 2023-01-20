---
title: 'Power of Two'
date: 2023-01-18
draft: false
github_link: ''
author: 'Ming Lee Ng'
tags:
  - LeetCode 231
  - Math
  - Bit Manipulation
  - Recursion
image: /images/blog/blog2.jpg
description: 'The Everyday Persons Guide to LeetCode #231'
toc:
socials:
---

## Introduction

Hello and welcome! I'm Ming Lee, and today we're going to cover **How to solve LeetCode 231 - Power of Two - in JS/TS :zap:**

Same as always we're gonna solve this, and we're gonna do it without the big fancy words because this is for regular folx! Keeping it nice and casual
round these parts! Movin' on...

## Problem

<b><a href='https://leetcode.com/problems/power-of-two'>`LeetCode 231 - Power of Two`</a></b>

Given an integer n, return true if it is a power of two. Otherwise, return false.

An integer n is a power of two, if there exists an integer x such that n == 2^x.

## Explanation

Ok, so this one is great for helping visualize some recursive functions. All we want to do is check to see if the number that we're currently looking
at is a power of two. Easy peasy. Let's keep in mind that 2 to the power of 0 is 1 before we start this whole ordeal.

Lets first start by adding another parameter to our function called power and set it to default as 0. From there we need to see if 2 ** power is ===
n. If so, return true. if 2 ** power is greater than n return false. If we make it past both of those then we can return isPowerOfTwo(n, power + 1).

This is going to make it so we start with n and check to see if 2 to the 0th power is n. Then 2 to the 1st then 2nd etc. Lets have a look at the code.

## Solution

```
function isPowerOfTwo(n: number, power = 0): boolean {
  const num = n ** power;
  if(num === n) return true;
  if(num > n) return false;

  return isPowerOfTwo(n, power + 1);
}
```

## Closing

This is a neat problem that we can solve with recursion. We could also use a regular for loop to solve this. If you're interested in trying to figure
out a mathy way to solve this without loops I recommend looking into logarithms. Alternatively, for those that are wanting to solve this without using
loops OR math, consider converting the number into binary. Once you print out all the numbers that return true in binary I think you'll notice some
similarities pretty quickly. Tomorrow we're going to look at handling a familiar kind of problem, just in reverse in
<a href='../implementqueueusingstacks/'>**`LeetCode 232 - Implement Queue Using Stacks`**</a>! See you then!
