---
title: 'Intersection of Two Arrays'
date: 2023-02-05
draft: false
github_link: ''
author: 'Ming Lee Ng'
tags:
  - LeetCode 349
  - Array
  - Hash Table
  - Two Pointers
  - Binary Search
  - Sorting
image: /images/blog/blog2.jpg
description: 'The Everyday Persons Guide to LeetCode #349'
toc:
socials:
---

## Introduction

Hello and welcome! I'm Ming Lee, and today we're going to cover **How to solve LeetCode 349 - Intersection of Two Arrays - in JS/TS :zap:**

Same as always we're gonna solve this, and we're gonna do it without the big fancy words because this is for regular folx! Keeping it nice and casual
round these parts! Movin' on...

## Problem

<b><a href='https://leetcode.com/problems/intersection-of-two-arrays/'>`LeetCode 349 - Intersection of Two Arrays`</a></b>

Given tow integer arrays nums1 and nums2, return an array of their intersection. Each element in the result must be unique and you may return the
result in any order.

## Explanation

Ok, so this is a cool one. We need to return where these two arrays 'intersect' but really all they're asking for is for us to return an array of
elements that are included in both nums1 and nums2, but without duplicates.

First of all, since we know that we need to exclude duplicates one of the first things that comes to mind should be Sets. Just to make this a little
easier on ourselves lets slap both nums1 and nums2 into two different Sets to start off with.

Now that we have our two Sets, lets iterate through the smaller of the two and if the larger set has the current element, we add it to a result array.

We don't necessarily have to iterate through the smaller array, we can iterate through either one, but I think it makes it a little easier to
visualize using the smaller one. Lets see how this might look in code.

## Solution

```
function intersection(nums1: number[], nums2: number[]): number[] {
  const result: number[] = [];
  const setA = new Set(nums1);
  const setB = new Set(nums2);

  if(setA.size < setB.size){
    for(const num of setA)
      if(setB.has(num)) result.push(num);
  } else {
    for(const num of setB)
      if(setA.has(num)) result.push(num);
  }

  return result;
}
```

## Closing

Good work! There are a few other ways that we can approach this problem, but this method is a pretty straight forward. Tomorrow's problem might give
you some more ideas on how to tackle this kind of stuff when we take a look at
<a href='../intersectionoftwoarraysii/'>**`LeetCode 350 - Intersection of Two Arrays II`**</a>! See you then!
