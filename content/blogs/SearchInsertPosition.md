---
title: 'Search Insert Position'
date: 2022-12-13
draft: false
github_link: ''
author: 'Ming Lee Ng'
tags:
  - LeetCode 35
  - Search Insert Position
  - Array
  - Binary Search
image: /images/blog/blog3.jpg
description: 'The Everyday Persons Guide to LeetCode #35'
toc:
socials:
---

## Introduction

Hello and welcome! I'm Ming Lee, and today we're going to cover **How to solve
LeetCode 35 - Search Insert Position - in JS/TS :zap:**

Same as always we're gonna solve this, and we're gonna do it without the big
fancy words because this is for regular folx! Keeping it nice and casual round
these parts! Movin' on...

## Problem

<b><a href='https://leetcode.com/problems/search-insert-position'>`LeetCode 35 - Search Insert Position`</a></b>

Given a sorted array of distinct integers and a target value, return the index
if the target is found. If not, return the index where it would be if it were
inserted in order.

You must write an algorithm with O(log n) runtime complexity.

## Explanation

Ok, so we are given a sorted array of numbers and we need to return either the
location of the number or the place where it would be inserted at. We also don't
want to just go though the array 1 at a time from start to end because that
would be too slow. One of the parts to this problem is that we must write
something that is O(log n) in time complexity. That means that we can't afford
to compare every single element. But since we know that this array is already
sorted we can do some fun stuff, like check the element in the middle. If the
element in the middle is the number we're looking for, we return that location.
Otherwise we start looking higher/lower depending on what number we did
encounter. To handle this kind of operation we'll declare a min and a max. If
our guess is too low then min will be set to that guess + 1. If our guess is too
high then we'll set our max to that guess - 1. We keep doing this guessing game
until we either locate the number or min becomes greater than max. Once min
becomes greater than max we know that the array does NOT contain the target, and
that the target really belongs between max and min, so we return min (where it
would be inserted at); It should look a little like the following in
implementation.

## Solution

```
function searchInsert(nums: number[], target: number): number {
    let min = 0,
        max = nums.length - 1;

    while(min <= max){
        const mid = Math.floor((min + max) / 2);
        if(nums[mid] === target) return mid;
        if(nums[mid] > target) max = mid - 1;
        else min = mid + 1;
    }

    return min;
}
```

## Closing

Outstanding! That's one of our first Binary Search type problems down! This is a
really fun problem to solve, but keep in mind that this is only possible because
we received a previously sorted array. Were were to have to sort the array
ourselves we could never achieve something as fast as O(n log) time complexity.
Regardless, this was a speedy and fun solution, and a great tool to have in the
bag! Next time we'll be tackling a slower-paced problem called
<a href='../lengthoflastword/'>**`LeetCode 58 - Length of Last Word`**</a>! See
you then!
