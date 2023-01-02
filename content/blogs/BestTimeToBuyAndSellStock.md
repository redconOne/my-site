---
title: 'Best Time to Buy and Sell Stock'
date: 2022-12-28
draft: false
github_link: ''
author: 'Ming Lee Ng'
tags:
  - LeetCode 121
  - Array
  - Dynamic Programming
image: /images/blog/blog3.jpg
description: 'The Everyday Persons Guide to LeetCode #121'
toc:
socials:
---

## Introduction

Hello and welcome! I'm Ming Lee, and today we're going to cover **How to solve LeetCode 121 - Best Time to Buy and Sell Stock - in JS/TS :zap:**

Same as always we're gonna solve this, and we're gonna do it without the big fancy words because this is for regular folx! Keeping it nice and casual
round these parts! Movin' on...

## Problem

<b><a href='https://leetcode.com/problems/best-time-to-buy-and-sell-stock'>`LeetCode 121 - Best Time to Buy and Sell Stock`</a></b>

You are given an array prices where prices[i] is the price of a given stock on the ith day.

You want to maximize your profit by choosing a single day to buy one stock and choosing a different day in the future to sell that stock.

Return the maximum profit you can achieve from this transaction. If you cannot achieve any profit, return 0.

## Explanation

Ok, so super common question here, and it seems a little difficult, but I know we've got this in the bag! What we're really wanting to do here is find
a day where we can buy low and eventually sell high. Now, we could go from element 0 thru the entire array comparing each number, then element 1 and
compare everything, but that takes a super long time. Fortunately, we have a better way to check this out!

First of all, we're gonna need two variables. One to track the current smallest number, and one to track the maximum profit. Lets name those something
like minPrice and maxProfit for clarity's sake.

Now, we need to iterate through every single number of the prices array, but we only need to do it one single time, so a for of will suffice here.
During that iteration we're going to want to check just a few things. First of all, if this number if smaller than minPrice, we've gotta set minPrice
to smaller. We always want to be working with the most recent small number.

The second thing we want to look for in our for loop is whether maxProfit less than num - smallest. If its smaller, then we have a new maxProfit, and
we need to update that variable!

Once we've finished iterating through the prices array we'll have the maximum profit stored in our maxProfit variable, so we just return that and
we're good to go!

## Solution

```

function maxProfit(prices: number[]): number {
  let minPrice = prices[0];
  let maxProfit = 0;

  for (const price of prices) {
    if (price < minPrice) minPrice = price;
    if (maxProfit < price - minPrice) maxProfit = price - minPrice;
  }

  return maxProfit;
}
```

## Closing

Niiice! This one is so fun once you get the hang of it! Make sure you take some time to really understand what we're doing, but just know that at the
end of the day all we're really doing is keeping track of two variables and iterating through the prices array. You've got this! Our next problem
should feel a little easier as its some basic string manipulation in <a href='../validpalindrome/'>**`LeetCode 125 - Valid Palindrome`**</a>!See you
then!
