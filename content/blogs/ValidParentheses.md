---
title: 'Valid Parentheses'
date: 2022-12-08
draft: false
github_link: ''
author: 'Ming Lee Ng'
tags:
  - LeetCode 20
  - Valid Parentheses
  - Strings
  - Stacks
image: /images/blog/blog2.jpg
description: 'The Everyday Persons Guide to LeetCode #20'
toc:
socials:
---

## Introduction

Hello and welcome! I'm Ming Lee, and today we're going to cover **How to solve
LeetCode 20 - Valid Parentheses - in JS/TS :zap:**

Same as always we're gonna solve this, and we're gonna do it without the big
fancy words because this is for regular folx! Keeping it nice and casual round
these parts! Movin' on...

## Problem

<b><a href='https://leetcode.com/problems/valid-parentheses'>`LeetCode 20 - Valid Parentheses`</a></b>

Given a string s containing just the characters **( ) { } [ ]** determine if the
input string is valid.

An input string is valid if:

Open brackets must be closed by the same type of brackets. Open brackets must be
closed in the correct order. Every close bracket has a corresponding open
bracket of the same type.

## Explanation

Cool, so this is a pretty fun one to solve. So we know that we can take in a ton
of opening brackets, but as soon as we hit a closing bracket - any of these: ) }
] - we need to verify that the LAST opening bracket matches. For this kind of
operation we need a data structure that handles First In Last Out kind of
operations, called FILO for short. Fortunately we can just use an Array for
this, but specifically we'll be using an array with push and pop ONLY to
simulate stack operations. Unshift and shift would be adding and removing from
the front of the stack, and we can't have that. So when we come across an
opening bracket of some sort we need to add the appropriate closing bracket to
our stack. When we hit a closing bracket we need to verify that it is the
closing bracket we were looking for by comparing it to the item on the top of
our stack. After we've gone through the entire string we then need to verify
that the stack is empty, aka all the opening parentheses were closed. It should
look a little something like this:

## Solution

```
const isValid = (str: string): boolean => {
  const stack: string[] = [];

  for(const bracket of str)
    switch(true){
        case bracket === '(':
            stack.push(')');
            break;
        case bracket === '{':
            stack.push('}');
            break;
        case bracket === '[':
            stack.push(']');
            break;
        default:
            const current = stack.pop();
            if(current !== bracket) return false;
            break;
    }

    return stack.length === 0;
};
```

## Closing

In this particular solution I utilized a switch statement, but feel free to
handle those comparisons any way you feel comfortable! There's nothing wrong
with using some ifs and elses in there! The important thing here is that you
learn how to think about things utilizing a Stack. Stacks are a pretty basic
data structure, and something that we'll definitely be seeing in the future, so
make sure you understand how they work! I like to think of them like a stack of
pancakes! You can always add another pancake on the top, but when it comes to
eating them, you eat the one on top first. The first pancake on the plate is the
last pancake eaten. Yum. Next on the chopping block is gonna be
<a href='../mergetwosortedlists/'>**`LeetCode 21 - Merge Two Sorted Lists`**</a>!
See you then!
