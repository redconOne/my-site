---
title: 'Merge Sorted Array'
date: 2022-12-20
draft: false
github_link: ''
author: 'Ming Lee Ng'
tags:
  - LeetCode 88
  - Array
  - Two Pointers
  - Sorting
image: /images/blog/blog1.jpg
description: 'The Everyday Persons Guide to LeetCode #88'
toc:
socials:
---

## Introduction

Hello and welcome! I'm Ming Lee, and today we're going to cover **How to solve LeetCode 88 - Merge Sorted Array - in JS/TS :zap:**

Same as always we're gonna solve this, and we're gonna do it without the big fancy words because this is for regular folx! Keeping it nice and casual
round these parts! Movin' on...

## Problem

<b><a href='https://leetcode.com/problems/merge-sorted-array'>`LeetCode 88 - Merge Sorted Array`</a></b>

You are given two integer arrays nums1 and nums2, sorted in non-decreasing order, and two integers m and n, representing the number of elements in
nums1 and nums2 respectively.

Merge nums1 and nums2 into a single array sorted in non-decreasing order.

The final sorted array should not be returned by the function, but instead be stored inside the array nums1. To accomodate this, nums1 has a length of
m + n, where the first m elements denote the elements that should be merged, and the last n elements are set to 0 and should be ignored. nums2 has a
length of n.

## Explanation

The instructions on this one are so long! It makes this sound a lot harder than its going to be though! The first thing that we need to know is that
we're not going to return anything. We're going to mutate nums1 and ensure that it contains both the values of nums1 and nums2, sorted in order. We're
also going to have a few pointers going at the same time, so its going to seem a little complicated, but don't worry, once we get the logic sorted out
it's going to be easy peasy!

First things first we need to realize that we're going to need to access both nums1 and nums2 at their "end" elements. Nums1 has m elements to be
added to the array and nums2 has n elements to be added, but arrays are accessed on a 0-based scale, so we'll need to decrement m and n before we do
anything.

Once we've decremented we need to iterate through the nums1 array. But here's the fun part. Instead of going from 0 -> nums1.length - 1 lets go the
other way around and go from nums1.length - 1 -> 0. So now that we know that i is starting at nums1.length - 1, we need to work on how long to
iterate. We want to iterate while i is greater than or equal to 0. Also if n runs out of elements we want to quit as well, but we'll address that
later. After each iteration we're going to decrement i. That's all three parts of the for loop!

Once we're inside the for loop we need to set up a conditional. We want to check and see if nums1[m] > nums2[n]. If so we will set nums1[i] to
nums1[m] and decrement m. Else we'll set nums1[i] to nums2[n] and decrement n. Now when we're considering these arrays there is a possibility for n to
be -1 while m >= 0. In that case we would try to make a comparison of nums1[m] > nums2[-1]. That's not a valid comparison, so we need to only continue
the for loop if i >= 0 && n >= 0.

After we exit the for loop we're done! And it we don't even need to return so that makes things even easier!

## Solution

```
function merge(nums1: number[], m: number, nums2: number[], n: number): void {
  m--;
  n--;

  for(let i = nums1.length - 1; i >= 0 && n >= 0; --i)
    if(nums1[m] > nums2[n])
      nums1[i] = nums1[m--];
    else
      nums1[i] = nums2[n--];
}
```

## Closing

Congrats on keeping up! This was a fun Two Pointer type problem, and a little bit of a brain-bender the first time you come across it! Don't worry
though, it should get a easier bit by bit with more and more practice! Tomorrow's problem will involve us working on the infamous Binary Trees! They
can be a complicated and intimidating data structure, but we're gonna keep it simple and tackle it no problemo in **`(coming soon)`**

<!-- <a href='../binarytreeinordertraversal/'>**`LeetCode 94 - Binary Tree Inorder Traversal`**</a>!  -->

See you then!
