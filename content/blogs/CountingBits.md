---
title: 'Counting Bits'
date:
draft: false
github_link: ''
author: 'Ming Lee Ng'
tags:
  - LeetCode 338
  - Dynamic Programming
  - Bit Manipulation
image: /images/blog/blog1.jpg
description: 'The Everyday Persons Guide to LeetCode #338'
toc:
socials:
---

## Introduction

Hello and welcome! I'm Ming Lee, and today we're going to cover **How to solve LeetCode 338 - Counting Bits - in JS/TS :zap:**

Same as always we're gonna solve this, and we're gonna do it without the big fancy words because this is for regular folx! Keeping it nice and casual
round these parts! Movin' on...

## Problem

<b><a href='https://leetcode.com/problems/counting-bits/'>`LeetCode 338 - Counting Bits`</a></b>

Given an integer n, return an array ans of length n + 1 such that for each i (0 <= i <= n), ans[i] is the number of 1's in the binary representatino
of i.

## Explanation

Ok. What a rough one to read. But what they're asking for isn't so bad. So what they want is for us to take the number n (lets pretend its 5 in this
case) and return the number of 1's for each binary number from 0 -> n.

So in our example with 5 we would check the following: 0,1,2,3,4,5. Lets look at a short table to see what the binary and number of 1's looks like.

| number | binary | no. of 1's |
| ------ | ------ | ---------- |
| 0      | 0      | 0          |
| 1      | 1      | 1          |
| 2      | 10     | 1          |
| 3      | 11     | 2          |
| 4      | 100    | 1          |
| 5      | 101    | 2          |

So in the above example we would return [0,1,1,2,1,2] from the entire function. So now that we know what they're asking for, how do we handle this?

Well first thing we need to do is create an array to hold our results in. From there we need to iterate from 0 -> n, so it sounds like a for loop will
suffice.

Inside the for loop we need to convert the iterator (i) to a binary number. We can handle that with toString(2). Then we need to count the number of
1's in that string. An easy way to handle that is to split this string into an array, then filter out the zeros and return the length. We push that
length into the result array.

After the loop is complete we simply return result. The code should look a little something like the following.

## Solution

```
function countBits(n: number): number[] {
  const result: number[] = [];

  for(let i = 0; i <= n; ++i)
    result.push(i.toString(2).split('').filter(x => +x).length);

  return result;
}
```

## Closing

There it is! Another confusing word problem solved! Tomorrow we're visiting another "power of" kind of problem in
<a href='../poweroffour/'>**`LeetCode 342 - Power of Four`**</a>! See you then!
