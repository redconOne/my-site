---
title: 'Summary Ranges'
date: 2023-01-17
draft: false
github_link: ''
author: 'Ming Lee Ng'
tags:
  - LeetCode 228
  - Array
image: /images/blog/blog1.jpg
description: 'The Everyday Persons Guide to LeetCode #228'
toc:
socials:
---

## Introduction

Hello and welcome! I'm Ming Lee, and today we're going to cover **How to solve LeetCode 228 - Summary Ranges - in JS/TS :zap:**

Same as always we're gonna solve this, and we're gonna do it without the big fancy words because this is for regular folx! Keeping it nice and casual
round these parts! Movin' on...

## Problem

<b><a href='https://leetcode.com/problems/summary-ranges'>`LeetCode 228 - Summary Ranges`</a></b>

You are given a sorted unique integer array nums.

A range [a,b] is the set of all integers from a to b (inclusive).

Return the smallest sorted list of ranges that cover all the numbers in the array exactly. That is, each element of nums is covered by exactly one of
the ranges, and there is no integer x such that x is in one of the ranges but not in nums.

Each range [a,b] in the list should be output as:

- "a->b" if a != b
- "a" if a == b

## Explanation

Ok, so here we are with another really wordy problem, but definitely something we can handle. What we're looking at here is a sorted array and we need
to ensure if we find numbers in a series, like 1,2,3 we need to replace those numbers with the a string "1->3". If the number is not part of a series
it will get added to the result as an individual char.

So considering all the above lets try and handle this. The first thing I like to do here is establish an array to hold our result string. We also need
to declare a variable to hold some kind of accumulator and another to hold the start of our range. The goal is going to be to iterate through the
array, checking to see if the nums[i] == startOfRange + acc. If so, we just need to increment our acc and move on. If nums[i] falls outside of our
range we need to make some pushes to result. So to start us off lets instantiate our accumulator at 1 and our startOfRange as nums[0].

Now on to our loop. Our loop is going to require us to iterate each element, but we already have nums[0] as startOfRange, so lets start with i = 1. We
will need to continue while i <= nums.length (More on this later), and we will increment i by one after each loop. Lets get that for loop goin!

Now inside the for lets make some real magic happen. if(nums[i] !== startOfRange + acc) we need to do things. This is the event where nums[i] falls
outside the range. So here, if(acc > 1) we need to push a range. So we push {startOfRange}->{startOfRange + acc - 1} using the accumulator to find the
last known number within the range. if acc <= 1 we just need to push {startOfRange} to result. After either of those instances we're going to need to
set startOfRange to nums[i] and acc to 1.

if(nums[i] === startOfRange + acc) then we know that nums[i] falls within our current range, so we simply increment acc and move on.

Because we're continuing to iterate as i <= nums.length this will handle the final range. If we do not do this we will be missing the last element of
the result array because we are still expecting more numbers. This will allow our loop to kind of "sort itself out" by running one more time than we
kind of think that we need to. If that sounds a little strange try running i < nums.length and i <= nums.length and see what the difference in the
result array is and try and think of why its that way. Alright, I think that's enough talk, lets see some code!

## Solution

```
function summaryRanges (nums: number[]): string[] {
  const result: string[] = [];
  let startOfRange = nums[0];
  let acc = 1;

  for(let i = 1; i <= nums.length; ++i)
    if(nums[i] !== startOfRange + acc){
      if(acc > 1) result.push(`${startOfRange}->${startOfRange + acc - 1}`);
      else result.push(`${startOfRange}`);
      startOfRange = nums[i];
      acc = 1;
    } else acc++;

  return result;
}
```

## Closing

Great work! I love the way this is a basic array problem without any DS&A kind of work, but it really makes you think about what you're encountering
within the nums array! Tomorrow we're looking at a super cool problem involing some recursion in <a href='..//'>**`LeetCode 231 - Power of Two`**</a>!
See you then!
