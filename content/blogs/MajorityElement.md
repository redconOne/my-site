---
title: 'Majority Element'
date: 2023-01-05
draft: false
github_link: ''
author: 'Ming Lee Ng'
tags:
  - LeetCode 169
  - Array
  - Hash Table
  - Divide and Conquer
  - Sorting
  - Counting
image: /images/blog/blog2.jpg
description: 'The Everyday Persons Guide to LeetCode #169'
toc:
socials:
---

## Introduction

Hello and welcome! I'm Ming Lee, and today we're going to cover **How to solve LeetCode 169 - Majority Element - in JS/TS :zap:**

Same as always we're gonna solve this, and we're gonna do it without the big fancy words because this is for regular folx! Keeping it nice and casual
round these parts! Movin' on...

## Problem

<b><a href='https://leetcode.com/problems/majority-element'>`LeetCode 169 - Majority Element`</a></b>

Given an array nums of size n, return the majority element.

The majority element is the element that appears more than ⌊n / 2⌋ times. You may assume that the majority element always exists in the array.

## Explanation

Ok, so this one is only asking you to find the number with the maximum amount of occurences within an array, and I think this is definitely do-able.
Now, we could do something like iterate through the array once, checking to see how many times element[0] occurs, then element[1], then element[2],
but that's super ineffecient. So instead lets try and use a dictionary type object to count the number of times we've seen a particular element as we
iterate through, and then we just find the largest number of occurences within that dictionary!

To start, we're gonna need to create an object to store key/value pairs.

After that step we need to iterate through every single element in the nums array, and only once. Because its just once I like to use a for of here,
but feel free to use your preferred method. We then check to see if the dictionary already has the item in question. If so, we increment it.
Otherwise, we instantiate it. So that should look a little something like this:

```
if(dict[x]) dict[x]++;
else dict[x] = 1;
```

Now from here we need to iterate through our dictionary and find the largest value, then return it's key. The code for this should look a little like
the following:

## Solution

```
function majorityElement (nums: number[]): number {
  const dict: { [key: number]: number } = {};

  for(let num of nums)
    if(dict[num]) dict[num]++;
    else dict[num] = 1;

  let bigNum = -1;
  let bigVal = 0;

  for(let key in dict)
    if(bigVal < dict[key]){
      bigVal = dict[key];
      bigNum = +key;
    }

  return bigNum;
}
```

## Closing

Good job! This was a nice and chill problem, especially in comparison to many of the other DS&A / mathy type of questions we've been working on for
the past few days. Tomorrow we'll be revisiting another excel type problem in
<a href='../excelsheetcolumnnumber/'>**`LeetCode 171 - Excel Sheet Column Number`**</a>! See you then!
