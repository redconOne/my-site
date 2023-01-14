---
title: 'Contains Duplicate'
date: 2023-01-13
draft: false
github_link: ''
author: 'Ming Lee Ng'
tags:
  - LeetCode 217
  - Array
  - Hash Table
  - Sorting
image: /images/blog/blog3.jpg
description: 'The Everyday Persons Guide to LeetCode #217'
toc:
socials:
---

## Introduction

Hello and welcome! I'm Ming Lee, and today we're going to cover **How to solve LeetCode 217 - Contains Duplicate - in JS/TS :zap:**

Same as always we're gonna solve this, and we're gonna do it without the big fancy words because this is for regular folx! Keeping it nice and casual
round these parts! Movin' on...

## Problem

<b><a href='https://leetcode.com/problems/contains-duplicate'>`LeetCode 217 - Contains Duplicate`</a></b>

Given an integer array nums, return true if any value appears at least twice in the array, and return false if every element is distinct.

## Explanation

Alright! This one should feel pretty comfortable if you've been doing all the other problems we've been taking a look at. Here we're looking at a
problem where we just need to see if there are two+ instances of any element in an array. We can pretty easily do this in quadratic time complexity by
going to each element and verifying that indexOf === lastIndexOf, but can we do it faster? Well, one faster way to handle things would be to sort the
array and then compare nums[i] with nums[i+1]. That gives us an n log n time complexity, but can we get it down to just a linear time complexity? We
sure can!

So first we need to declare a hashmap to store our data in. It will be storing numbers as keys and booleans as values.

We then need to iterate over every element in nums. If the dictionary contains the element, return true because there is at least 1 duplicate. If the
dictionary doesn't contain the element add that element to the dictionary (set the boolean value as True).

Once we've iterated through nums without finding a duplicate we return false. And we've iterated nums only once, so we're at a linear time complexity!

## Solution

```
function containsDuplicate(nums: number[]): boolean {
  const dict: { [key: number]: boolean } = {};

  for(const num of nums)
    if(dict[num]) return true;
    else dict[num] = true;

  return false;
}
```

## Closing

Nice! Good job on this one, but this was just the little guy. We'll be taking another look at arrays and duplicates when we handle the big boss of
this little snake of a problem in <a href='../containsduplicateii/'>**`LeetCode 218 - Contains Duplicate II`**</a>! See you then!
