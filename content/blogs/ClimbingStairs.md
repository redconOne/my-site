---
title: 'Climbing Stairs'
date: 2022-12-18
draft: false
github_link: ''
author: 'Ming Lee Ng'
tags:
    - LeetCode 70
    - Climbing Stairs
    - Math
    - Dynamic Programming
    - Memoization
image: /images/blog/blog2.jpg
description: 'The Everyday Persons Guide to LeetCode #70'
toc:
socials:
---

## Introduction

Hello and welcome! I'm Ming Lee, and today we're going to cover **How to solve LeetCode 70 - Climbing Stairs - in JS/TS :zap:**

Same as always we're gonna solve this, and we're gonna do it without the big fancy words because this is for regular folx! Keeping it nice and casual
round these parts! Movin' on...

## Problem

<b><a href='https://leetcode.com/problems/climbing-stairs'>`LeetCode 70 - Climbing Stairs`</a></b>

You are climbing a staircase. It takes n steps to reach the top.

Each time you can either climb 1 or 2 steps. In how many distinct ways can you climb to the top?

## Explanation

Ok folx, so this one is gonna be a little funky, so hang on for the ride! There's kind of a neat pattern that happens here, and one of the hints of
the puzzle is to look at the previous number of steps. So lets take that into consideration. If n = 1 we know there is only 1 step. Because there's
only one step we can only climb in uh... one step. If n = 2 we know there are 2 steps. We can either climb one at a time OR just climb both steps at
once. So there are 2 ways to the top for 2 steps. Here's where we start to see a kind of pattern. When n = 3 we can climb one at a time, 1 step then 2
steps, or 2 steps then 1 step. So a total of 3. See the pattern? If not, that's ok, we'll go one more. If n = 4 there are a total of four steps. We
can climb in the following ways 1+1+1+1, 2+2, 1+1+2, 1+2+1, or 2+1+1. There are a total of 5 ways to make it to the top.

Lets tidy this up and look at it in a table. Maybe with a few more inputs as well.

| n   | ways to climb |
| --- | ------------- |
| 1   | 1             |
| 2   | 2             |
| 3   | 3             |
| 4   | 5             |
| 5   | 8             |
| 6   | 13            |
| 7   | 21            |
| 8   | 34            |
| 9   | 55            |
| 10  | 89            |

This ought to help make the pattern a little more visible. For each n the way to climb is the previous number of ways to climb + the previous previous
number of ways to climb. For example, at 6 steps, we need to add the ways to climb of 4 and 5, which are 5 and 8, to give us a total of 13. Now that
we see this pattern, the implementation should be a lot easier! First we'll handle some edge cases. If n is less than 3 we just need to return n.
Otherwise we need to start iterating.

Now, during the iteration we need to continue updating our "previous" step by setting it to previous + its previous. To help with this I'll name them
something like closeBehind being the step right behind us, and farBehind, being the step behind that. So lets first consider making a temp variable to
hold closeBehind, then do some closeBehind += farBehind action. Then we can set farBehind = temp.

That's enough crazy talk, lets look at some code.

## Solution

```
function climbStairs(n: number): number {
    if(n < 3) return n;

    let farBehind = 0,
        closeBehind = 1;

    for(let i = 1; i < n; i++){
        const temp = closeBehind;
        closeBehind += farBehind;
        farBehind = temp;
    }

    return closeBehind + farBehind;
}
```

## Closing

Great job! This one was a little mathy, but we managed to handle it with a little pattern recognition. Tomorrow's problem should be a little less
mathy as we're looking at solving another Linked List type problem, namely:
<a href='../removeduplicatesfromsortedlist/'>**`LeetCode 83 - Remove Duplicates from Sorted List`**</a>! See you then!
