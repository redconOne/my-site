---
title: "Pascal's Triangle"
date: 2022-12-26
draft: false
github_link: ''
author: 'Ming Lee Ng'
tags:
  - LeetCode 118
  - Array
  - Dynamic Programming
image: /images/blog/blog1.jpg
description: 'The Everyday Persons Guide to LeetCode #118'
toc:
socials:
---

## Introduction

Hello and welcome! I'm Ming Lee, and today we're going to cover **How to solve LeetCode 118 - Pascals Triangle - in JS/TS :zap:**

Same as always we're gonna solve this, and we're gonna do it without the big fancy words because this is for regular folx! Keeping it nice and casual
round these parts! Movin' on...

## Problem

<b><a href='https://leetcode.com/problems/pascals-triangle'>`LeetCode 118 - Pascal's Triangle`</a></b>

Given an integer numRows, return the first numRows of Pascal's Triangle. In Pascal's Triangle, each number is the sum of the two numbers directly
above it as shown below:

```
        1
      1   1
    1   2   1
  1   3   3   1
1   4   6   4   1

```

## Explanation

So this looks really simple at a glance, but it can be kind challenging to actually implement, and that's totally ok! The first thing we're gonna do
is get ready to store a bunch of values by creating an array. We know that numRows is going to be greater than 1 (because of our constraints) so we
will start there with our result being a nested array like this [[1]]

Now that we've handled the case where numRows === 1 we need to handle all the other possibilities! So lets start a for loop and make sure that we set
i = 1 because we already accounted for the starting case. The loop will continue as long as i < numRows, and we'll increment i after every iteration.

Now during this loop is where we start the magic. We'll need to make an array, I name mine row, to hold the numbers of the row that we're currently
building. I like to create an array that holds the previous row as well, and I name that one previous. Once we've done that, we're gonna need to
iterate over previous.

For the second loop we'll set j to 0 and increment by one. We're really just looking to check every single element within our previous array. For each
element we want to push(previous[j] + previous[j - 1]) to our row. But if j is 0 we can't add previous[j - 1] so we'll go ahead and slap an || on that
part and use a 0. It should look something like this: row.push(prev[j] + (prev[j-1] || 0))

Now we're done with that nested for loop. So while we're still inside the first for, but completely outside of the second for loop we want to push(1)
to row. This just adds a 1 to the end of row which is a good thing because we're always gonna end each row with a new 1. We then push the row into
result, and we'll have ourselves a nice neat triangle when its all said and done! The final code should look a little like this...

## Solution

```
function generate(numRows: number): number[][] {
  let result: number[][] = [[1]];

  for (let i = 1; i < numRows; ++i) {
    const row: number[] = [];
    const prev = result[i - 1];

    for (let j = 0; j < prev.length; ++j) row.push(prev[j] + (prev[j - 1] || 0));

    row.push(1);
    result.push(row);
  }

  return result;
}

```

## Closing

There we go! This one is was kinda mathy, kinda not, but hang on tight because we're dealing with more Pascal's Triangle craziness in tomorrow's
problem <a href='../pascalstriangleii/'>**`LeetCode 119 - Pascal's Triangle II`**</a>!See you then!
