---
title: 'Plus One'
date: 2022-12-15
draft: false
github_link: ''
author: 'Ming Lee Ng'
tags:
  - LeetCode 66
  - Plus One
  - Array
  - Math
image: /images/blog/blog2.jpg
description: 'The Everyday Persons Guide to LeetCode #66'
toc:
socials:
---

## Introduction

Hello and welcome! I'm Ming Lee, and today we're going to cover **How to solve
LeetCode 66 - Plus One - in JS/TS :zap:**

Same as always we're gonna solve this, and we're gonna do it without the big
fancy words because this is for regular folx! Keeping it nice and casual round
these parts! Movin' on...

## Problem

<b><a href='https://leetcode.com/problems/plus-one'>`LeetCode 66 - Plus One`</a></b>

You are given a large integer represented as an integer array digits, where each
digits[i] is the ith digit of the integer. The digits are ordered from most
significant to least significant in left-to-right order. The large integer does
not contain any leading 0's.

Increment the large integer by one and return the resulting array of digits.

## Explanation

This is such a cool problem conceptually! I love it! Basically we're just given
a number that is split up into an array and we have to add 1 to that number!
Now, its easy to look at this kind of problem and think hey, I can just join
these together into a string, cast it into a Number, add one, string it, split
it, cast into number and return! That's a totally valid way of approaching this
problem, with one exception. We're gonna be getting some rather large numbers
here, and that doesn't necessarily work out for us using those kinds of
operations (unless we do things like using BigInt). We're gonna have to get a
little more funky with it to come up with a real solution. The first thing I
like to do is reverse digits. It just makes it a little easier for me to work
with, but adds to time complexity and doesn't really need to be done, so take
that with a grain of salt. So now that we have our digits array reversed, we
just need to increment the 0th position by one. Now the whole process has really
started. In the event the last digit of digits was the number 9, we need to be
prepared to increment other numbers within the digits array to prevent them from
exceeding 2 digits in size. In other words, no digit may be larger than the
number 9 within the array. I like to handle this by creating a "carry over" kind
of variable. It can be a boolean or a number. I think case I think we'll use a
number.

Now when it comes to checking this array I like to loop through the whole darn
thing starting at 0. If digits[i] + carry is greater than 9, we got ourselves a
problem. In that event we need to set digit[i] to digits[i] - 10 (feel free to
use modulo here if you wish) and we need to set carry to 1 so it carries over to
the next digit. In the event we're no longer carrying anything over (aka carry
=== 0) we can just return digits.reverse() because we're not really doing any
more math. After we make it through the entire loop there's still one more carry
to account for, so we push(1), then return digits.reverse().

That was kind of a mouthful, and I think viewing the actual code might make it
make a little more sense, so let's have a looksie.

## Solution

```
function plusOne (digits: number[]): number[] {
    // just to make things easier
    digits.reverse();
    digits[0]++;

    let carry = 0;

    // to check to make sure all these are less than 10
    for(let i = 0; i < digits.length; ++i){
        digits[i] += carry;
        if(digits[i] > 9) carry = 1;
        else return digits.reverse();
        digits[i] -= 10;
    }

    // handle additional carry over
    digits.push(1);

    return digits.reverse();
}
```

## Closing

Awesome! This is a perfectly functioning plus one! We do a lot of fun stuff in
this particular solution, and we can make it even more fun by doing things like
handling this without using reverse, handling this without using a carry over
variable, or using BigInt. I hope everyone is feeling pretty comfortable about
this solution because tomorrow's is going to be in a very similar vein as we
look to solve <a href='../addbinary/'>**`LeetCode 67 - Add Binary`**</a>! See
you then!
