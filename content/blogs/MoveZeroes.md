---
title: 'Move Zeroes'
date: 2023-01-27
draft: false
github_link: ''
author: 'Ming Lee Ng'
tags:
  - LeetCode 283
  - Array
  - Two Pointers
image: /images/blog/blog2.jpg
description: 'The Everyday Persons Guide to LeetCode #283'
toc:
socials:
---

## Introduction

Hello and welcome! I'm Ming Lee, and today we're going to cover **How to solve LeetCode 283 - Move Zeroes - in JS/TS :zap:**

Same as always we're gonna solve this, and we're gonna do it without the big fancy words because this is for regular folx! Keeping it nice and casual
round these parts! Movin' on...

## Problem

<b><a href='https://leetcode.com/problems/move-zeroes/'>`LeetCode 283 - Move Zeroes`</a></b>

Given an integer array nums, move all 0's to the end of it while maintaining the relative order of the non-zero elements.

Note that you must do this in-place without making a copy of the array.

## Explanation

Ok, so here we need to move all the non-zero numbers to the front of the array, keeping them in the same order, and then have all the zeroes at the
end of the array. We don't return anything, and we make sure to mutate the array that we're given. No problemo!

So lets take a really easy approach to this. We can handle this with two pointers. One pointing to positions that need to mutate, and one that is
iterating one element at a time searching for non-zero numbers.

One of the simplest ways to handle this is to create a new variable that will hold the total number of non-zero elements within the array. I like to
create that like this:

```
let nonZeroes = nums.filter(num => num).length;
```

Now we can proceed to make a for loop to iterate through the array. When declaring variables we'll need something to track the index of all the
elements in the array like normally, lets call it i. We also need a variable to track the current 'to be mutated' location. Lets call it k. It should
look a little like the following:

```
for(let i = 0, k =0; i < nums.length; ++i)
```

Now during this loop if nums[i] is 0 we don't actually need to do anything. So in that case we just need to continue. But if nums[i] is non-zero we
have a few things to handle. If nums[i] is nonzero we need nums[k] to equal nums[i]. We then set nums[i] = 0 if i is greater than or equal to
nonZeroes. What this will do is ensure that if we encounter a number it is moved appropriately, and that the elements in the last portion of the array
<= our previously calculated nonZero number will all be set to 0. Lets take a look at how this will all be in its entirety.

## Solution

```
function moveZeroes(nums: number): void {
  let nonZeroes = nums.filter(num => num).length;

  for(let i = 0, k = 0; i <= nums.length; ++i){
    if(nums[i] === 0) continue;
    nums[k] = nums[i];
    if(i <= nonZeroes) nums[i] = 0;
  }
}
```

## Closing

Great job! This a super fun two-pointer / array problem. There are tons of different ways to handle this, some without involving the first iterator in
the problem. Try seeing if you can figure out how to make this faster than it currently is! We'll be looking at
<a href='../wordpattern/'>**`LeetCode 290 - Word Pattern`**</a>! See you then!
