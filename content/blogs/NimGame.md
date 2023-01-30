---
title: 'Nim Game'
date: 2023-01-29
draft: false
github_link: ''
author: 'Ming Lee Ng'
tags:
  - LeetCode 292
  - Math
  - Brainteaser
  - Game Theory
image: /images/blog/blog1.jpg
description: 'The Everyday Persons Guide to LeetCode #292'
toc:
socials:
---

## Introduction

Hello and welcome! I'm Ming Lee, and today we're going to cover **How to solve LeetCode 292 - Nim Game - in JS/TS :zap:**

Same as always we're gonna solve this, and we're gonna do it without the big fancy words because this is for regular folx! Keeping it nice and casual
round these parts! Movin' on...

## Problem

<b><a href='https://leetcode.com/problems/nim-game/'>`LeetCode 292 - Nim Game`</a></b>

You are playing the following Nim game with your friend:

- Initially, there is a heap of stones on the table.
- You anre your friend will alternate taking turns and you go first.
- On each turn, the person whose turn it is will remove 1 to 3 stones from the heap.
- The one who removes the last stone is the winner.

Given n, the number of stones in the heap, return true if you can win the game assuming both you and your friend play optimally, otherwise return
false.

## Explanation

Ok, so this one sounds really complicated, but its not as bad as you think it is! We just need to find scenarios where we are able to win. So lets
think about this. Because we're able to take away anywhere from 1-3 stones, if we start with less than three we auto win. There's one condition that
we're pretty certain of.

We also know that for the number 4, no matter what we play we will lose. If we play 1 there are 3 left and our friend takes those three and we lose.
Similar for if we take away 2 or 1. So starting with 4 is a losing proposition.

What about 5? We could take one, leaving our friend with 4. We know from the previous scenario that if a player is confronted with 4 stones they will
lose. We we just forced a loss to our friend there. With 6 we can take away 2 to give them a 4. With 7 we take 3.

But here's something interesting. If we started with 8 stones there is nothing we can do to avoid our friend giving us a 4, given optimal play. So
we're doomed to lose at 4 and 8... what about 12? At 12 we also lose. So now we can safely assume that we lose when given a set of stones that is
divisible by 4. Now that we know this simple rule we should be able to write this code pretty quickly! Lets see the solution below

## Solution

```
function canWinNim(n: number): boolean {
  return n % 4 !== 0;
}
```

## Closing

What a fun one! This is a shorty mathy one, but its really fun to work out and think of the game. We're heading back into some work with arrays next
when we work on <a href='..//'>**`LeetCode 303 - Range Sum Query - Immutable`**</a>! See you then!
