---
title: 'Add Binary'
date: 2022-12-16
draft: false
github_link: ''
author: 'Ming Lee Ng'
tags:
  - LeetCode 67
  - Add Binary
  - Math
  - String
  - Bit Manipulation
  - Simulation
image: /images/blog/blog3.jpg
description: 'The Everyday Persons Guide to LeetCode #67'
toc:
socials:
---

## Introduction

Hello and welcome! I'm Ming Lee, and today we're going to cover **How to solve
LeetCode 67 - Add Binary - in JS/TS :zap:**

Same as always we're gonna solve this, and we're gonna do it without the big
fancy words because this is for regular folx! Keeping it nice and casual round
these parts! Movin' on...

## Problem

<b><a href='https://leetcode.com/problems/add-binary'>`LeetCode 67 - Add Binary`</a></b>

Given two binary strings a and b, return their sum as a binary string.

## Explanation

So this problem does require us to know how binary works, but don't worry, its
fairly simple to get a rudimentary understanding of binary. To start, we need to
recognize that it only has 2 numbers, 0 and 1. The numbering system most of us
are used to using is called decimal, which has 10 numbers. 0-9. In decimal, when
we get to the number 9 and increment, we have to add to a new column, the "tens"
column. Once the tens column has used all 10 digits and we need to increment
further we introduce a "hundreds" column and so on and so forth. Its actually
just as simple when we're using binary! I'll produce a table to help explain.

| Decimal | Binary |
| ------- | ------ |
| 0       | 0      |
| 1       | 1      |
| 2       | 10     |
| 3       | 11     |
| 4       | 100    |
| 5       | 101    |
| 6       | 110    |
| 7       | 111    |
| 8       | 1000   |
| 9       | 1001   |
| 10      | 1010   |
| 11      | 1011   |

Now that we have a kind of understanding of how binary works we can use that to
help us handle this problem. For this we just need to add both of these string'd
numbers together. If the number is 0 or 1 that's totally fine. If the
combination adds up to 2, we set that digit to 0 and use a carry over to add to
the next digit. If the numbers and carry over add up to 3 then we set the digit
to 1 AND send a carry over to the next digit. That might sound a little
confusing, but trust me, it'll make a little more sense when we see it in code
so just hang tight for that. Also, because we're doing addition we typically
start our work from right to left. To assist us in making that a little easier,
we'll be reversing both of the strings to make it a little easier to work with.
Now lets have a look at this code!

## Solution

```
function addBinary(str1: string, str2: string): string {
    str1 = str1.split('').reverse().join('');
    str2 = str2.split('').reverse().join('');

    let result = '',
        carry = 0;

    for(let i = 0; i < str1.length || i < str2.length; ++i){
        const current = (+str1[i] || 0) + (+str2[i] || 0) + carry;
        result = current % 2 ? 1 + result : 0 + result;
        carry = current > 1 ? 1 : 0;
    }

    return carry ? 1 + result : result;
}
```

## Closing

Nice! So this is definitely one of my most favorite problems. We get to play
around with binary, which I super enjoy, and we get to use some fun ternary
operators as well! Try giving it a shot and playing around with new ways to
handle this problem! You could handle the results in the form of an array or in
a string like we're using here. We could handle things with ternary's, ifs, or
even a switch statement! It's all programmer's preference, and there's nothing
wrong with doing things differently than others! You've got this! Tomorrow we'll
be workin on <a href='../sqrtx/'>**`LeetCode 69 - Sqrt(x)`**</a>! See you then!
