---
title: 'Excel Sheet Column Title'
date: 2023-01-04
draft: false
github_link: ''
author: 'Ming Lee Ng'
tags:
  - LeetCode 168
  - Math
  - String
image: /images/blog/blog1.jpg
description: 'The Everyday Persons Guide to LeetCode #168'
toc:
socials:
---

## Introduction

Hello and welcome! I'm Ming Lee, and today we're going to cover **How to solve LeetCode 168 - Excel Sheet Column Title - in JS/TS :zap:**

Same as always we're gonna solve this, and we're gonna do it without the big fancy words because this is for regular folx! Keeping it nice and casual
round these parts! Movin' on...

## Problem

<b><a href='https://leetcode.com/problems/excel-sheet-column-title'>`LeetCode 168 - Excel Sheet Column Title`</a></b>

Given an integer columnNumber, return its corresponding column title as it appears in an Excel sheet.

## Explanation

Ok, this is definitely a fun one, but it can feel a bit tricky so prepare yourself for a little bit of a mathy experience here.

First things first, this problem is asking us to take numbers and convert them into a series of characters. A = 1, B = 2, Z = 26 AA = 27, AB = 28, AZ
= 52

So when we look at this we know that if the number is 26 or less, this is pretty simple. We just need to either uses a string or charcodes or
something to handle the generation of the result. I like to use a string like this: const values = 'ABCDEFGHJIKLMNOPQRSTUVWXYZ';

So now, when the program is input with a number less than 26 we just need to do values.indexOf(num - 1) and that's our result! But what if the number
is larger than 26? Well then we need to do some mathing.

So to work on the number 27 or higher first we need to address the 'ones' place. So lets just knock off everything except for the bottom 26 by doing
(columnNumber % 26). We can then use the result from that variable with values to add to our output. Except there's one problem there... we're used to
dealing with 0 as a starting point, whether its in binary or decimal, but in this particular case, A is the first element. To handle the lack of 0's
we need to subtract one during operations. If you fail to account for the lack of zero you're gonna have off-by-one errors all day.

Now that we've gotten a character added to our result let's adjust columnNumber. We're gonna need to decrement it, divide it by 26, and parse that as
an integer (just Math.floor it).

So that will look something like this columnNumber = Math.floor((columnNumber - 1) / 26)

We need to continue doing these operations taking characters worth of numbers from columnNumber over and over until columnNumber === 0. At that point
we return the result we've built up. The working code should look a little something like this:

## Solution

```
function convertToTitle(columnNumber: number): string {
  const values = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ';
  let result = '';

  while(columnNumber){
    result = values[(columnNumber - 1) % 26] + result;
    columnNumber = Math.floor((columnNumber - 1) / 26);
  }

  return result;
}
```

## Closing

This one was a bit mathy, so don't worry if the first pass feels a little rough. Give it some time. Take a break, walk around the block, come back and
try to take a look at it again! It should make more and more sense as times goes on. The more we deal with hexadecimal and binary the more frequently
we're going to do stuff like this, so this kind of mathy operation will definitely appear again (and soon), but its not so frequent that if you're a
little hazy you should be intimidated or upset. We'll get a bit of a break from this kinda stuff when we look at tomorrow's problem,
<a href='../majorityelement/'>**`LeetCode 169 - Majority Element`**</a>! See you then!
