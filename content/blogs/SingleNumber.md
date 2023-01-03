---
title: 'Valid Palindrome'
date: 2022-12-30
draft: false
github_link: ''
author: 'Ming Lee Ng'
tags:
  - LeetCode 136
  - Array
  - Bit Manipulation
image: /images/blog/blog2.jpg
description: 'The Everyday Persons Guide to LeetCode #136'
toc:
socials:
---

## Introduction

Hello and welcome! I'm Ming Lee, and today we're going to cover **How to solve LeetCode 136 - Single Number - in JS/TS :zap:**

Same as always we're gonna solve this, and we're gonna do it without the big fancy words because this is for regular folx! Keeping it nice and casual
round these parts! Movin' on...

## Problem

<b><a href='https://leetcode.com/problems/single-number'>`LeetCode 136 - Single Number`</a></b>

Given a non-empty array of integers nums, every element appears twice except for one. Find that single one.

You must implement a solution with a linear runtime complexity and use only constant extra space.

## Explanation

Ok, so at a glance we know that we can solve this kind of problem by iterating through all the elements of the array and checking to see if indexOf
that number is === lastIndexOf. But the problem with that is that indexOf and lastIndexOf are both linear in complexity and unfortunately that means
that using them inside a for loop would make this quadradic in time complexity. So we're gonna have to pass on that one.

Another excellent way to solve this problem is with hashmaps, as I'm sure many of you have already considered. Hashmaps are a great way to handle
this, but unfortunately that would result in use of linear space, which also isn't great. So unfortunately we're really not looking to use that here
either.

What we're really supposed to be doing here is hinted at in the "related topics" section. We should be considering using some kind of bit manipulation
to solve this. Now, normally when we're talking about bits or boolean type of operations we think of things like ORs or ANDs. But there are others
that we don't use quite as freqently. One of which is XOR (exclusive OR). The cool thing about this particular operator is that it looks a little like
the following table.

| A     | B     | RESULT |
| ----- | ----- | ------ |
| false | false | false  |
| false | true  | true   |
| true  | false | true   |
| true  | true  | false  |

As you can see here, it looks like a totally normal OR, except for in the case where both A AND B are true. Then it returns false! We require
specifically ONLY 1 of these elements to be true. If both are true, it cancels itself out.

Armed with this knowledge we can try and use XOR to solve this in a pretty fun way! We can create a new variable, lets call it result, and set it
to 0. From there, we can just iterate one single time through nums, XORing that number into result. It should look a little something like this:
result ^= num. Lets take a look at another table and see what would happen here using the example where nums is [4, 1, 2, 1, 2]

| result before | num | result after | explanation    |
| ------------- | --- | ------------ | -------------- |
| 0             | 4   | 4            | add 4          |
| 4             | 1   | 5            | add 1          |
| 5             | 2   | 7            | add 2          |
| 7             | 1   | 6            | 1's cancel out |
| 6             | 2   | 4            | 2's cancel out |

## Solution

```

function isPalindrome(str: string): boolean {
  str = str.toLowerCase().replace(/[^a-z0-9]/g, '');
  return str === str.split('').reverse().join('');
}
```

## Closing

Good work! After all the crazy problems we've done this one should be a little more straight forward to wrap your brain around. Don't be discouraged
if there are a few bugs to work out though, that's completely normal! We'll have another straight-forward problem tomorrow when we address solving
<a href='../singlenumber/'>**`LeetCode 136 - Single Number`**</a>! See you then!
