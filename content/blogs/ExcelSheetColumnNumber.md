---
title: 'Excel Sheet Column Number'
date: 2023-01-06
draft: false
github_link: ''
author: 'Ming Lee Ng'
tags:
  - LeetCode 171
  - Math
  - String
image: /images/blog/blog2.jpg
description: 'The Everyday Persons Guide to LeetCode #171'
toc:
socials:
---

## Introduction

Hello and welcome! I'm Ming Lee, and today we're going to cover **How to solve LeetCode 171 - Excel Sheet Column Number - in JS/TS :zap:**

Same as always we're gonna solve this, and we're gonna do it without the big fancy words because this is for regular folx! Keeping it nice and casual
round these parts! Movin' on...

## Problem

<b><a href='https://leetcode.com/problems/excel-sheet-column-number'>`LeetCode 171 - Excel Sheet Column Number`</a></b>

Given a string columnTitle that represents the column title as appears in an Excel sheet, return its corresponding column number.

## Explanation

So for those of you that have used excel before this should sound pretty straightforward. For everyone else it might take some time to wrap your head
around things. Basically, ever column in an excel spreadsheet is referenced from A - Z. After Z it goes from AA - AZ. Then to BA-BZ. etc etc.

So we're gonna have to get a little mathy here. First of all, each character is representing a "place". In the number 10 we think of 1 as being in the
"tens" place and 0 as being in the "ones" place. Lets think of these columns as something similar. But instead of having the numbers 0-9 to choose
from we have A-Z, 26 characters total. Now, because those are all representing values 1-26 I like to make a string and do an indexOf to tell me what
that value is. So let's take a look at the following string

```
const values = ' ABCDEFGHIJKLMNOPQRSTUVWXYZ';
```

In this string, if you do values.indexOf('A') you get 1 and if you do values.indexOf('B') you get 26. Excellent! So this can handle all columns that
are only 1 character long! But what if there are two characters, like AA or AZ? Well that's where things get a little funny.

To handle more "places" we'll need to make a variable to account for such a thing. We can make a places variable and set it to zero. There are 26
characters, and 26 to the power of zero is 1. So for a the column A we can view A as the following:

```
values.indexOf('A') * 26 ** 0
values.indexOf('A') * 1
1 * 1
1
```

Then, after we check a "place" we can increment places to handle the next digit. So if we're looking at something like 'AZ' it should look like this:

```
values.indexOf('Z') * 26 ** 0
values.indexOf('Z') * 1
26 * 1
26

values.indexOf('A') * 26 ** 1
values.indexOf('A') * 26
1 * 26
26

'AZ' = 26 + 26
```

Ok. Hopefully that's at the very least as clear as mud. Let's try implementing this and see how it looks. Keep in mind that due to the nature of the
"places" we're going to want to iterate through the string in reverse for this solution. We could do it without, but lets keep this as simple as
possible for the first pass through, ok? Here we go!

## Solution

```
function titleToNumber(column: string): number {
  const values = ' ABCDEFGHIJKLMNOPQRSTUVWXYZ';
  let result = 0;
  let place = 0;

  for (let i = column.length - 1; i >= 0; --i, ++place) result += values.indexOf(column[i]) * 26 ** place;

  return result;
}
```

## Closing

This one was a bit mathy, so don't worry if the first pass feels a little rough. Give it some time. Take a break, walk around the block, come back and
try to take a look at it again! It should make more and more sense as times goes on. The more we deal with hexadecimal and binary the more frequently
we're going to do stuff like this, so this kind of mathy operation will definitely appear again, but its not so frequent that if you're a little hazy
you should be intimidated or upset. We are going to get a little more practice with it in tomorrow's problem,
<a href='../reversebits/'>**`LeetCode 190 - Reverse Bits`**</a>! See you then!
