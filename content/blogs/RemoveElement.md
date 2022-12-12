---
title: 'Remove Element'
date: 2022-12-12
draft: false
github_link: ''
author: 'Ming Lee Ng'
tags:
  - LeetCode 27
  - Remove Element
  - Array
  - Two Pointers
image: /images/blog/blog2.jpg
description: 'The Everyday Persons Guide to LeetCode #27'
toc:
socials:
---

## Introduction

Hello and welcome! I'm Ming Lee, and today we're going to cover **How to solve
LeetCode 27 - Remove Element - in JS/TS :zap:**

Same as always we're gonna solve this, and we're gonna do it without the big
fancy words because this is for regular folx! Keeping it nice and casual round
these parts! Movin' on...

## Problem

<b><a href='https://leetcode.com/problems/remove-element'>`LeetCode 27 - Remove Element`</a></b>

Given an integer array nums and an integer val, remove all occurrences of val in
nums in-place. The relative order of the elements may be changed.

Since it is impossible to change the length of the array in some languages, you
must instead have the result be placed in the first part of the array nums. More
formally, if there are k elements after removing the duplicates, then the first
k elements of nums should hold the final result. It does not matter what you
leave beyond the first k elements.

Return k after placing the final result in the first k slots of nums.

Do not allocate extra space for another array. You must do this by modifying the
input array in-place with O(1) extra memory.

## Explanation

For those of you that came from yesterday's problem (Remove Duplicates From
Sorted Array) this should look and sound really familiar! For those of us that
haven't, don't worry about it because we're about to take a nice long look at
how to solve this. So keeping in mind that we want to change the array that was
given to us and not return a whole new array, we need loop through every element
in the array, changing them to new values if they are one of the target values.
The goal is to return a number value, held by pointer, where numbers 0 - pointer
are NOT val. All the numbers from pointer + 1 - the end of nums are irrelevant
and we don't care what value they are.

With that in mind, lets create a pointer variable set to 0. We then want to
iterate through every element of the nums array. If that particular number is
not equal to val, we set nums[pointer] to that number and then increment
pointer. If it IS equal to val, we continue and do nothing.

After the iteration and changing of all the values we will return pointer. Lets
look at this in a table format. All of these values are going to be as if they
were printed out in a console.log() as the first thing in for loop. The example
array will be [1,2,2,3,4,2,2,5,6], and the value we're removing will be 2

| pointer | i   | nums[i] | nums                |
| ------- | --- | ------- | ------------------- |
| 0       | 0   | 1       | [1,2,2,3,4,2,2,5,6] |
| 1       | 1   | 2       | [1,2,2,3,4,2,2,5,6] |
| 1       | 2   | 2       | [1,2,2,3,4,2,2,5,6] |
| 1       | 3   | 3       | [1,2,2,3,4,2,2,5,6] |
| 2       | 4   | 4       | [1,3,2,3,4,2,2,5,6] |
| 3       | 5   | 2       | [1,3,4,3,4,2,2,5,6] |
| 3       | 6   | 2       | [1,3,4,3,4,2,2,5,6] |
| 3       | 7   | 5       | [1,3,4,3,4,2,2,5,6] |
| 4       | 8   | 6       | [1,3,4,5,4,2,2,5,6] |

After the final iteration pointer will be at 5 and nums will look like
[1,3,4,5,6,2,2,5,6]

## Solution

```
function removeElement(nums: number[], val: number): number {
    let pointer = 0;

    for(let i = 0; i < nums.length; ++i)
        if(nums[i] !== val){
            nums[pointer] = nums[i];
            pointer++;
        }

    return pointer;
}
```

## Closing

Excellent work! There's another Two Pointer solution in the bag! Assuming you've
handled both Remove Duplicates and Remove Element at this point you should be
feeling a little more comfortable with Two Pointers! Which is great because this
is definitely a skill that we'll be using futher up the road! But next time,
instead of two pointers, we'll look at dividing and conquering with a Binary
Search problem in
<a href='../searchinsertposition/'>**`LeetCode 35 - Search Insert Position`**</a>!
See you then!
