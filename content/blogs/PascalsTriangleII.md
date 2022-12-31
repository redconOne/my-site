---
title: "Pascal's Triangle II"
date: 2022-12-27
draft: false
github_link: ''
author: 'Ming Lee Ng'
tags:
  - LeetCode 119
  - Array
  - Dynamic Programming
image: /images/blog/blog2.jpg
description: 'The Everyday Persons Guide to LeetCode #118'
toc:
socials:
---

## Introduction

Hello and welcome! I'm Ming Lee, and today we're going to cover **How to solve LeetCode 119 - Pascals Triangle II - in JS/TS :zap:**

Same as always we're gonna solve this, and we're gonna do it without the big fancy words because this is for regular folx! Keeping it nice and casual
round these parts! Movin' on...

## Problem

<b><a href='https://leetcode.com/problems/pascals-triangle-ii'>`LeetCode 119 - Pascal's Triangle II`</a></b>

Given an integer rowIndex, return the rowIndexth (0-indexed) row of the Pascal's triangle.

## Explanation

Ok, so in this one, instead of returning a massive array of rows it just wants to see the final row that would be generated.

With that in mind, lets go ahead and handle the smallest scenario. We know that we might have to handle a 0 this time, but rowIndex 0 would just
return the first row of [1]. So lets start by creating a result array with the number 1 in it.

We also need to iterate rowIndex number of times, so lets set up a loop to do that, starting at 1

For each time our first for loop iterates we'll want a second for loop. The second for will go through the current 'row' that is being worked on, aka
result, and make some adjustments. Now here's where things get a little spicy. This second for loop is going to start at position i, decrement each
iteration, and will continue as long as j is greater than 0. This is just going to make sure that we iterate i number of times.

Now within the second for loop is where we're doing all our heavy lifting. Here we want to set result at j to equal to result[j] + result[j - 1]. So
each element is going to be equal to itself plus the previous. This is going to handle the creation of the next row. But there is the possibility that
result[j] is undefined, so we'll make sure to handle that with (result[j] || 0)

After both for loops have finished we can return result and we're good to go!

## Solution

```

function getRow(rowIndex: number): number[] {
  const result = [1];

  for(let i = 1; i <= rowIndex; ++i)
    for(let j = i; j > 0; --j)
      result[j] = (result[j] || 0) + result[j - 1];

  return result;
}

```

## Closing

Alright, it works! We can all let out that sigh of relief now, we're done with Pascal's Triangle! Super funky problems, but fun to work with! Next
we'll be working on a super common interview question
<a href='../besttimetobuyandsellstock/'>**`LeetCode 121 - Best Time to Buy and Sell Stock`**</a>!See you then!
