---
title: 'Sqrt (x)'
date: 2022-12-17
draft: false
github_link: ''
author: 'Ming Lee Ng'
tags:
    - LeetCode 69
    - Sqrt (x)
    - Math
    - Binary Search
image: /images/blog/blog1.jpg
description: 'The Everyday Persons Guide to LeetCode #69'
toc:
socials:
---

## Introduction

Hello and welcome! I'm Ming Lee, and today we're going to cover **How to solve LeetCode 69 - Sqrt (x) - in JS/TS :zap:**

Same as always we're gonna solve this, and we're gonna do it without the big fancy words because this is for regular folx! Keeping it nice and casual
round these parts! Movin' on...

## Problem

<b><a href='https://leetcode.com/problems/sqrtx'>`LeetCode 69 - Sqrt (x)`</a></b>

Given a non-negative integer x, return the square root of x rounded down to the nearest integer. The returned integer should be non-negative as well.

You must not use any built-in exponent function or operator.

For example, do not use pow(x, 0.5) in c++ or x \*\* 0.5 in python.

## Explanation

Ok, so this time we'll take this problem on in two different ways. The first way will be a little more simple and the second way will be a little more
smarty pants. So we know that we're given a positive number and we need to return the square root of it rounded down to the nearest integer. That
means that if there is no perfect square root, we need to return the closest approximation. No problemo! So if we consider the simple solution, we can
just iterate until we find that perfect sweet spot. If the number times itself is equal to x, then we're done! If its greater than x we need to return
the previous digit. It should look a little something like this.

## Solution

```
function mySqrt(x: number): number {
    for(let i = 0; i <= x; ++i)
        if(i * i === x) return i;
        else if(i * i > x) return i - 1;

    return 0;
}
```

## Refactor Explanation

Now the above solution works, and it works just fine. It hands cases where x is 0 or super large. The problem is that we go from 0 -> 1 -> 2 and so
on. Its linear, and kinda slowish. Is there a way to speed it up? You betcha. Because we're essentially dealing with a bunch of sorted numbers, we can
utilize a binary search! That changes our runtime from O(n) to O(log n) which is gonna be a good bit better! So to set that up we first need to handle
a left limit, which we know will be 1 (we have to do this to account for the cases where x is 0), and we need a right limit, which can just be x + 1
(we havet to set to x + 1 to account for cases where x is 1).

Now that we have left and right limits set, we can work on a while loop. While left is less than right, we created a mid. The mid will be left+right
/ 2. We'll also round down to the nearest integer here with a Math.floor(). If x / mid === mid then we know that x has a perfect square and that mid
is it! So we just return mid.

If x / mid > mid then we know that we're thinking too small here, and we can eliminate every number below mid. That's half of the numbers gone
already! We'll just set left to mid + 1 and run again!

If x / mid < mid then the opposite is true and we're guessing too high. We'll just set right to mid and keep on keepin on! In the event left becomes
larger than right, we break out of the loop. In this case we now know that left is just one element larger than the number we need, so we just return
min - 1 and we're good to go, simple as that.

That might sound like a lot of mathy stuff, and it kind of is, but hopefully the code will kind of clear things up. Here's what the Binary Search of
sqrt(x) would look like:

## Refactor Solution

```
function mySqrt(x: number): number {
    let left = 1;
    let right = x + 1;

    while(left < right){
        const mid = Math.floor((left + right) / 2);

        if(x / mid === mid) return mid;
        if(x / mid > mid) left = mid + 1;
        if(x / mid < mid) right = mid;
    }

    return left - 1;
}
```

## Closing

Nice! We managed to learn two different ways to solve sqrt(x), and we got to implement a really cool binary search for a logn solution for one of
them! Super cool! Tomorrow's solution is gonna be a little bit of a thinky thinky brain bender, so prepare yourself for some mental stair climbing as
we handle <a href='../climbingstairs/'>**`LeetCode 70 - Climbing Stairs`**</a>! See you then!
