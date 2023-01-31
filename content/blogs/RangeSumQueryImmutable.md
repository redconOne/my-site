---
title: 'Range Sum Query Immutable'
date: 2023-01-30
draft: false
github_link: ''
author: 'Ming Lee Ng'
tags:
  - LeetCode 303
  - Array
  - Design
  - Prefix Sum
image: /images/blog/blog2.jpg
description: 'The Everyday Persons Guide to LeetCode #303'
toc:
socials:
---

## Introduction

Hello and welcome! I'm Ming Lee, and today we're going to cover **How to solve LeetCode 303 - Range Sum Query Immutable - in JS/TS :zap:**

Same as always we're gonna solve this, and we're gonna do it without the big fancy words because this is for regular folx! Keeping it nice and casual
round these parts! Movin' on...

## Problem

<b><a href='https://leetcode.com/problems/range-sum-query-immutable/'>`LeetCode 0001 - Range Sum Query Immutable`</a></b>

Given an integer array nums, handle multiple queries of the following type:

Calculate the sum of the elements of nums between indices left and right inclusive where left <= right.

Implement the NumArray class:

- NumArray(int[] nums) initializes the object with the integer array nums.

- int sumRange(int left, int right) returns the sum of the elements of nums between indices left and right inclusive (i.e. nums[left]] + nums[left +
  1] + ... + nums[right]).

## Explanation

Ok, so this one is yet another problem where the problem sounds massively more difficult than it actually is. So basically all they are asking for is
a new object called NumArray where we can call a function sumRange. The sum range function is supposed to return the sum of all elements from left ->
right.

So first things first we know that we need to create an object and it needs to be able to handle a number array as an argument in the constructor.
That should look a little something like this:

```
class NumArray {
  arr: number[];
  constructor(nums: number[]) {
    this.arr = nums;
  }
}
```

To finish this problem off we also need to create a function to sum a small segment, or slice, of this array. So lets implement that. We can access
our object's array with the keyword this, and from there we will slice the array from to right (inclusive). That should look something like the
following:

```
sumRange(left: number, right: number): number {
  const range = this.arr.slice(left, right + 1);
  return range.reduce((sum, num) => sum + num, 0);
}
```

Alltogether this should look something like the solution here

## Solution

```
class NumArray {
  arr: number[];
  constructor(nums: number[]) {
    this.arr = nums;
  }

  sumRange(left: number, right: number): number {
    const range = this.arr.slice(left, right + 1);
    return range.reduce((sum, num) => sum + num, 0);
  }
}
```

## Closing

Nice! That should have felt pretty good considering all the math and data-structures we've been covering! The hardest part of this type of question is
really just trying to figure out what the heck we need to get to work on in the first place. Next we'll be taking a look at
<a href='../powerofthree/'>**`LeetCode 326 - Power of Three`**</a>! See you then!
