---
title: 'Happy Number'
date: 2023-01-09
draft: false
github_link: ''
author: 'Ming Lee Ng'
tags:
  - LeetCode 202
  - Hash Table
  - Math
  - Two Pointers
image: /images/blog/blog2.jpg
description: 'The Everyday Persons Guide to LeetCode #202'
toc:
socials:
---

## Introduction

Hello and welcome! I'm Ming Lee, and today we're going to cover **How to solve LeetCode 202 - Happy Number - in JS/TS :zap:**

Same as always we're gonna solve this, and we're gonna do it without the big fancy words because this is for regular folx! Keeping it nice and casual
round these parts! Movin' on...

## Problem

<b><a href='https://leetcode.com/problems/happy-number'>`LeetCode 202 - Happy Number`</a></b>

Write an algoritm to determine if a number n is happy.

A happy number is a number defined by the following process:

- Starting with any positive integer, replace the number by the sum of the squares of its digits.
- Repeat the process until the number equals 1 (where it will stay), or it loops endlessly in a cycle which does not include 1.
- Those numbers for which this process ends in 1 are happy.

Return true if n is a happy number, and false if not.

## Explanation

Ok, so that's a complicated set of instructions! So we've gotta take a number, square all of its digits, then sum those numbers together. If those
digits summed together equal 1 we return true. If we've already encountered this number before we return false. If this is a new number to us and the
sum isn't 1 we need to recursively call ourselves. Hopefully those instructions make this make a little more sense!

So because we need to find a sum of a number's digits I like to convert the number into an array first. We can do that with a .toString().split('')
from here we can choose to map over the array and convert all the elements into numbers again, but I prefer to just handle that in the reduce step. So
all in all, to find the sum, I like to do something like toString().split('').reduce((sum, num) => sum + +num \*\* 2, 0) This will sum all the numbers
up, starting at the value 0, with each number being squared before being added. Perfect!

Now that we have the sum we just need to check and see if it is 1. If so, return true!

Assuming the sum isn't 1 we need to do some more checking. We need to see if we've encountered this number before, and there are a few ways to handle
that. I like to utilize an array here just for simplicity's sake. Feel free to use a dictionary, set, map, or whatever else. We can create this array
by setting a default arr = [] value as a parameter for this function. Check to see if arr.includes(total). If it does, we return false. If it doesn't
then we need to add total to the array and call ourselves again. All in all the code should look similar to the following.

## Solution

```
function isHappy(n: number, arr: number[] = []): boolean {
  const total = n.toString().split('').reduce((sum, num) => sum + +num ** 2, 0);

  if(total === 1) return true;
  if(arr.includes(total)) return false;

  arr.push(total);

  return isHappy(total, arr);
}
```

## Closing

There we go! This was a fun one, just doing some basic math operations, storing previous results, and recursively calling ourselves. This is a great
problem to revisit if you're feeling a little rusty with recursion! Don't worry if you're feeling math'd out because tomorrow we're headed right back
into Linked Lists in <a href='../removelinkedlistelements/'>**`LeetCode 203 - Remove Linked List Elements`**</a>! See you then!
