---
title: 'Contains Duplicate II'
date: 2023-01-14
draft: false
github_link: ''
author: 'Ming Lee Ng'
tags:
  - LeetCode 219
  - Array
  - Hash Table
  - Sliding Window
image: /images/blog/blog1.jpg
description: 'The Everyday Persons Guide to LeetCode #219'
toc:
socials:
---

## Introduction

Hello and welcome! I'm Ming Lee, and today we're going to cover **How to solve LeetCode 219 - Contains Duplicate II - in JS/TS :zap:**

Same as always we're gonna solve this, and we're gonna do it without the big fancy words because this is for regular folx! Keeping it nice and casual
round these parts! Movin' on...

## Problem

<b><a href='https://leetcode.com/problems/contains-duplicate-ii'>`LeetCode 219 - Contains Duplicate II`</a></b>

Given an interger array nums and an integer k, return true if there are two distinct indices i and j in the array such that nums[i] == nums[j] and
abs(i - j) <= k.

## Explanation

Ok that description left me a little dazed and confused on the first look, but its not nearly as bad as it at first sounds. All they want to know is
if there are duplicates within the array that are no further than k elements apart. So if we have an array [7, 1, 2, 3, 4, 5, 6, 7] and k is 2, even
though there are duplicates they are more than 2 elements apart from each other, so it doesn't count.

So there are a whole bunch of ways to solve this, but lets take a look at a really simple way to handle things. First we'll declare an array that is
going to handle k sized elements.

We then need to iterate over every number in nums. We can handle that with a for of in this case (or any other way, I just like for ofs). Then we
check to see if arr.includes(num). If so return true. If not, we'll push the num into arr. After the push if arr.length > k we need to knock the first
element off, so arr.shift().

If we've made it through all the elements of the nums without returning true we return false

## Solution

```
function containsNearbyDuplicate(nums: number[], k: number): boolean {
  const arr: number[] = [];

  for(const num of nums){
    if(arr.includes(num)) return true;

    arr.push(num)
    if(arr.length > k) arr.shift();
  }

  return false;
}
```

## Closing

Excellent! Now we've taken out the little guy by handling the regular old contains duplicate and the boss problem! Next we'll be taking a look at some
more data structures in <a href='../implementstackusingqueues/'>**`LeetCode 225 - Implement Stack using Queues`**</a>! See you then!
