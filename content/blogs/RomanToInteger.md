---
title: 'Roman to Integer'
date: 2022-12-07
draft: false
github_link:
author: 'Ming Lee Ng'
tags:
  - LeetCode 13
  - Roman to Integer
  - Hashmaps
  - Strings
image: /images/blog/blog3.jpg
description: 'The Everyday Persons Guide to LeetCode #13'
toc:
socials:
---

## Introduction

Hello and welcome everyone! I'm Ming Lee, and we'll be working on **How to solve
LeetCode 13 - Roman to Integer - in JS/TS :zap:**

We'll be doin' what we always do and working on solving this without any of the
big fancy words and keeping it casual. That said, if you do NOT know what roman
numerals are now is a good time to check them out ->
<a href='https://en.wikipedia.org/wiki/Roman_numerals'>**`Wikipedia`**</a>

## Problem

<b><a href='https://leetcode.com/problems/roman-to-integer'>`LeetCode 13 - Roman to Integer`</a></b>

Roman numerals are represented by seven different symbols: **I, V, X, L, C, D**
and **M**.

| <b>Symbol</b> | <b>Value</b> |
| ------------- | ------------ |
| I             | 1            |
| V             | 5            |
| X             | 10           |
| L             | 50           |
| C             | 100          |
| D             | 500          |
| M             | 1000         |

For example, 2 is written as II in Roman numeral, just two ones added together.
12 is written as XII, which is simply X + II. The number 27 is written as XXVII,
which is XX + V + II.

Roman numerals are usually written largest to smallest from left to right.
However, the numeral for four is not IIII. Instead, the number four is written
as IV. Because the one is before the five we subtract it making four. The same
principle applies to the number nine, which is written as IX. There are six
instances where subtraction is used:

I can be placed before V (5) and X (10) to make 4 and 9. X can be placed before
L (50) and C (100) to make 40 and 90. C can be placed before D (500) and M
(1000) to make 400 and 900. Given a roman numeral, convert it to an integer.

## Explanation

Awesome! So now we're ready to take a swing as this thing! So there are a ton of
different ways to solve this particular thing, but I personally love using a
hashmap (before the haters rise up yes, I know about Maps ). When considering
coding this lets think about how we want to handle things. We know that there
are seven chars that can be used (IVXLCDM) and that if we put a smaller value in
front of a larger one that we'll be subracting instead of adding. Armed with
that knowledge we know that we will only encounter 13 scenarios when iterating
through our string. We might come across something like V, and if that V is
preceeded by an I then its not really a 5, its a 4. So we need to pay special
attention to those pesky subtraction type scenarios. Once we create an object
that holds our key(string) : property(number) pairs, we can work on actually
solving this thing!

To tackle this we want to loop through every single key in our object. We can
easily handle this with a for-in loop. From there we can remove that key from
the roman numeral string and add the value to the result variable. Once we've
made it through all the keys in the object, we'll be done!

## Solution

```
function romanToInt(str: string): number {
    const values:{[key: string]:number} = {
        CM: 900,
        M: 1000,
        CD: 400,
        D: 500,
        XC: 90,
        C: 100,
        XL: 40,
        L: 50,
        IX: 9,
        X: 10,
        IV: 4,
        V: 5,
        I: 1
    };

    var result = 0;

    for(let key in values){
        while(str.includes(key)){
            str = str.replace(key, '');
            result += values[key];
        }
    }

    return result;
};
```

## Closing

And that's a working solution right there! This is probably one of my favorite
leetcodes as it involves a pretty basic concept, but it requires a little bit of
thinking to try and get things working properly. There are also tons of ways to
solve this, and its always neat to see what other people come up with. Don't
worry if this one felt kinda funky, because tomorrow's should feel a little
easier to work with. We'll be looking at coding a solution for
<a href='../longestcommonprefix/'>**`LeetCode 14 - Longest Common Prefix`**</a>.
See you there!
