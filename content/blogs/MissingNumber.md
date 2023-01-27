---
title: 'Missing Number'
date: 2023-01-25
draft: false
github_link: ''
author: 'Ming Lee Ng'
tags:
  - LeetCode 268
  - Array
  - Hash Table
  - Math
  - Binary Search
  - Bit Manipulation
  - Sorting
image: /images/blog/blog3.jpg
description: 'The Everyday Persons Guide to LeetCode #268'
toc:
socials:
---

## Introduction

Hello and welcome! I'm Ming Lee, and today we're going to cover **How to solve LeetCode 268 - Missing Number - in JS/TS :zap:**

Same as always we're gonna solve this, and we're gonna do it without the big fancy words because this is for regular folx! Keeping it nice and casual
round these parts! Movin' on...

## Problem

<b><a href='https://leetcode.com/problems/missing-number/'>`LeetCode 268 - Missing Number`</a></b>

Given an array nums containing n distinct numbers in the range [0, n], return the only number in the range that is missing from the array.

## Explanation

Ok, so in this one we have a list of numbers from 0 thru x and and we need to find the one that's missing. Now we can pretty easily handle this by
doing something like starting a for loop at 0 and searching to see if nums.includes(i) This will totally work. But because we're doing and includes
inside of a for loop we're looking at a quadratic time here.

Now there is a fun way to handle this one thats a little faster. What if we looped through the entire array, adding all the numbers up? If we have an
array like this [0, 1, 3, 4] we can easily see that the 2 is missing. If we add the numbers up we get 8. Now, if while we were iterating through that
loop we were adding i + 1 to another variable we would be adding a kind of expected group of values together. The i + 1 variable, after looping once,
is 10. So we have 10 in expected and 8 in the array's total values. 10 - 8 is 2, and that happens to be the value that is missing. We handle this
solution in one single loop, so we're looking at linear o(n) runtime, which is way better! Lets take a look at how the code might appear:

## Solution

```
function missingNumber(nums: number[]): number {
  let arrTotal = 0;
  let expected = 0;

  for(let i = 0; i < nums.length; ++i) {
    expected += i + 1;
    arrTotal += i;
  }

  return expected - arrTotal;
}
```

## Closing

There we go! That was a super fun one, and the solution is pretty neat. What changes would you make? Keep playing around until you find a solution
that makes sense for you! We're working on an excellent question tomorrow in <a href='../firstbadversion/'>**`LeetCode 278 - First Bad Version`**</a>!
See you then!
