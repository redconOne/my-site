---
title: 'First Bad Version'
date: 2023-01-26
draft: false
github_link: ''
author: 'Ming Lee Ng'
tags:
  - LeetCode 278
  - Binary Search
  - Interactive
image: /images/blog/blog1.jpg
description: 'The Everyday Persons Guide to LeetCode #278'
toc:
socials:
---

## Introduction

Hello and welcome! I'm Ming Lee, and today we're going to cover **How to solve LeetCode 278 - First Bad Version - in JS/TS :zap:**

Same as always we're gonna solve this, and we're gonna do it without the big fancy words because this is for regular folx! Keeping it nice and casual
round these parts! Movin' on...

## Problem

<b><a href='https://leetcode.com/problems/first-bad-version/'>`LeetCode 278 - First Bad Version`</a></b>

You are a product manager and currently leading a team to develop a new product. Unfortunately, the latest version of your product fails the quality
check. Since each versino is developed based on the previous version, all the versions after a bad version are also bad.

Suppose you have n version [1, 2, ..., n] and you want to find out the first bad one, which causes all the following ones to be bad.

You are given an API bool isBadVersion(version) which returns wheter a version is bad. Implement a function to find the first bad version. You should
minimize the number of calls to the API.

## Explanation

Ok, this is a super fun one because we have an "API" that we can call to verify data in this one! We know that we need to find the first version where
isBadVersion will return true and to try and make as few API calls as possible.

So because this is a 1 based versioning lets start with 1 and end with n. To reduce the number of API calls, lets use a Binary Search. We'll start our
search right in the middle point, which will be Math.floor((n - 1) / 2). From here we verify if the middle is a bad version or not. If so, we need to
set n to mid - 1. Else we need to set start to mid + 1. We want to continue doing this while start is less than or equal to n. At some point start
will be larger, and thats exactly the point that we want to return! Lets see how that looks in code.

## Solution

```
const solution = function(isBadVersion: any) {
  return function(n: number): number {
    let start = 1;
    let end = n;

    while(start <= end) {
      const mid = Math.floor((start + end) / 2);
      if(isBadVersion(mid)) end = mid - 1;
      else start = mid + 1;
    }

    return start;
  }
}
```

## Closing

This one is a lot of work to understand, but I think the more you use it and the more you see it things will start to make sense. This is a fun one to
use Binary Search on, and it massively limits the number of calls we're making to the "API" here. We'll be working with arrays in the next problem,
<a href='../movezeroes/'>**`LeetCode 283 - Move Zeroes`**</a>! See you then!
