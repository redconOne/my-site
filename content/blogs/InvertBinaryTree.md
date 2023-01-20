---
title: 'Invert Binary Tree'
date: 2023-01-16
draft: false
github_link: ''
author: 'Ming Lee Ng'
tags:
  - LeetCode 226
  - Strings
image: /images/blog/blog3.jpg
description: 'The Everyday Persons Guide to LeetCode #226'
toc:
socials:
---

## Introduction

Hello and welcome! I'm Ming Lee, and today we're going to cover **How to solve LeetCode 226 - Invert Binary Tree - in JS/TS :zap:**

Same as always we're gonna solve this, and we're gonna do it without the big fancy words because this is for regular folx! Keeping it nice and casual
round these parts! Movin' on...

## Problem

<b><a href='https://leetcode.com/problems/invert-binary-tree'>`LeetCode 226 - Invert Binary Tree`</a></b> Given the root of a binary tree, invert the
tree, and return its root.

## Explanation

Ok, so all we're wanting to do to 'invert' this binary tree is swap its left <-> right branches. But then for the left and right branches we also need
to recursively call the swap on the new left/right branches as well. That way the tree looks like a complete mirror image of what it used to be.

So first things first, we already know that if root is null we'll return null. This is a pretty standard base case for binary trees, so you should be
familiar with how this looks, but just in case you aren't, we'll be using something like if(!root) return null;

Once we've made it past the base case we need to return a new TreeNode with its left node as inverseTree(root.right) and left node as
inverseTree(root.left).

That's actually the entire problem all right there! Lets take a look at how it is in TypeScript.

## Solution

```
function invertTree (root: TreeNode | null): TreeNode | null {
  if(!root) return null;

  return new TreeNode(root.val, invertTree(root.right), invertTree(root.left));
}
```

## Closing

Wow that was a quick one! Nice, short, easy, and good for some tree/recursion practice! I love it! Next we'll be looking at a super cool array problem
in <a href='..//'>**`LeetCode 228 - Summary Ranges`**</a>! See you then!
