---
title: 'Two Sum'
date: 2022-12-05T11:14:58+05:30
draft: false
github_link: ''
author: 'Ming Lee Ng'
tags:
  - LeetCode 1
  - Two Sum
  - Hashmaps
image:
description: 'The Everyday Persons Guide to LeetCode #1'
toc:
socials:
---

## Introduction

Hello and welcome! I'm Ming Lee, and today I'll be covering: **How to solve
LeetCode 1 - Two Sum - in JS/TS :zap:**

But we're not just going to cover it using a bunch of fancy terms and key words
that are going to require a lot of googling. This blog post, and all the ones to
follow, are meant for the casual programmer, the people who want to finish a
coding challenge, but have a real life to get back to as well. We're gonna
swerve any fancy words and break it down into easy explainable pieces.

## Problem

<b><a href="https://leetcode.com/problems/two-sum">`LeetCode 1 - Two Sum`</a></b>

Given an array of integers **nums** and an integer **target**, return indices of
the two numbers such that they add up to **target**.

You may assume that each input would have **exactly one solution**, and you may
not use the same element twice.

You can return the answer in any order.

## Explanation

Cool cool. So in normal person speak that means we need to loop through the
array searching for two locations, where those locations contain numbers that
add up to our target. Easy peasy. The first thing thing we'll work on is looping
through the nums array. Then we want to check value by value to see if there is
a complimentary value that adds up to the target within nums, and that the two
values are both at different locations. Sounds pretty straight forward, so lets
give it a shot!

If you're doing this in traditional JavaScript don't get intimidated by the
funky looking TypeScript here. Just ignore everything after the colons and
you'll be AOK.

## Solution

```
function twoSum(nums: number[], target: number): number[] {
  for(const idx in nums){
    const num = nums[idx]
    const comp = nums.indexOf(target - num);
    if(comp !== -1 && comp !== +idx) return [+idx, comp]
  }

  return [];
}
```

## Refactor Explanation

Now this **works** but we're looking at a quadratic time complexity, which is
kinda yikes here. Is there a way for us to bring it down to something more
linear? Perhaps. JavaScript does provide us with Maps to operate at a constant
speed with! So if we look at things with that in consideration, we can do cool
stuff like loop through nums, and see if our map **has** the complementary
number that we need. If it does, we'll just return that element's index as well
as the index we're currently at. If it does not contain what we need, we just
add the current value to the map as a key with the index as a property. Oh, and
for all my JavaScript folx remember to ignore any colons and the types that
follow them, but also don't use the < > brackets between Map(). Vanilla JS folx
can just use = new Map() instead. That said, the solution should look something
like the following.

## Refactor Solution

```
function twoSum(nums: number[], target: number): number[] {
  const map = new Map<number, number>();

    for(const idx in nums){
        const num = nums[idx];
        const comp = target - num;

        if(map.has(comp)) return [map.get(comp), +idx];
        map.set(num, +idx);
    }

    return []
}
```

And there we have it! A short and sweet Two Sum function! Unlike our first
attempt this one is a little more effecient, going from quadratic o(n^2) to
linear o(n). Nice! That's the first LeetCode down! Now, from here, we could
continue on to LeetCode 2, which is Add Two Numbers, but, despite that one being
pretty fun, it is also a medium difficulty, which I think we'll save for a bit
later. Lets instead look forward to tackling
<a href='/PalindromeNumber.md'>LeetCode 9 - Palindrome Number</a> next. See you
then!
