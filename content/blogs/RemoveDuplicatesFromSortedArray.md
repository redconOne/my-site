---
title: 'Remove Duplicates from Sorted Array'
date: 2022-12-11
draft: false
github_link: ''
author: 'Ming Lee Ng'
tags:
  - LeetCode 26
  - Remove Duplicates from Sorted Array
  - Array
  - Two Pointers
image: /images/blog/blog1.jpg
description: 'The Everyday Persons Guide to LeetCode #26'
toc:
socials:
---

## Introduction

Hello and welcome! I'm Ming Lee, and today we're going to cover **How to solve
LeetCode 26 - Remove Duplicates from Sorted Array - in JS/TS :zap:**

Same as always we're gonna solve this, and we're gonna do it without the big
fancy words because this is for regular folx! Keeping it nice and casual round
these parts! Movin' on...

## Problem

<b><a href='https://leetcode.com/problems/remove-duplicates-from-sorted-array'>`LeetCode 26 - Remove Duplicates from Sorted Array`</a></b>

Given an integer array nums sorted in non-decreasing order, remove the
duplicates in-place such that each unique element appears only once. The
relative order of the elements should be kept the same.

Since it is impossible to change the length of the array in some languages, you
must instead have the result be placed in the first part of the array nums. More
formally, if there are k elements after removing the duplicates, then the first
k elements of nums should hold the final result. It does not matter what you
leave beyond the first k elements.

Return k after placing the final result in the first k slots of nums.

Do not allocate extra space for another array. You must do this by modifying the
input array in-place with O(1) extra memory.

## Explanation

Okie dokie! This one should be pretty straight-forward. We'll be looking at
handling this buy looping through the nums array with one pointer holding a
current index and one pointer holding the index of where the next non-repeating
number belongs. That might sound funky, but its pretty fun to implement. Lets
consider the following example : nums = [1,2,2,3,4,4,5] The goal is for nums to
be [1,2,3,4,5, x, x], where those last two x's can be whatever number in the
world, we really just don't care. So we can start with our pointer at 0 and
start iterating through nums. If nums[i] is not equal to nums[i + 1] then we
want to set nums[pointer] to nums[i] and then increment pointer.

So considering the example [1,2,2,3,4,4,5] lets look at the following table as
what would be console.logged if we printed these variables as the very first
operation within our for loop.

| pointer | i   | nums[i] | nums[i + 1] | nums            |
| ------- | --- | ------- | ----------- | --------------- |
| 0       | 0   | 1       | 2           | [1,2,2,3,4,4,5] |
| 1       | 1   | 2       | 2           | [1,2,2,3,4,4,5] |
| 1       | 2   | 2       | 3           | [1,2,2,3,4,4,5] |
| 2       | 3   | 3       | 4           | [1,2,2,3,4,4,5] |
| 3       | 4   | 4       | 4           | [1,2,3,3,4,4,5] |
| 3       | 5   | 4       | 5           | [1,2,3,3,4,4,5] |
| 4       | 6   | 5       | undefined   | [1,2,3,4,4,4,5] |

Ok. Now after all the elements have been looped through and we've got elements
0-pointer as non-duplicates, we can just return the pointer as per the problems
instructions. A full implementation of the code should look like the following:

## Solution

```
function removeDuplicates (nums: number[]): number {
  let pointer = 0;

  for(let i = 0; i < nums.length; ++i)
    if(nums[i] !== nums[i + 1]){
      nums[pointer] = nums[i];
      pointer++;
    }

  return pointer;
}
```

## Closing

Awesome! This was a pretty fun solution involving Two Pointers. The two pointer
concept is something that will be revisisted in the future, so if this something
that you like then you're in luck because tomorrow's problem will be yet another
two pointer type problem!
<a href='../removeelement/'>**`LeetCode 27 - Remove Element`**</a>! See you
then!
