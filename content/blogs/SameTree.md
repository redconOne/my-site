---
title: 'Same Tree'
date: 2022-12-22
draft: false
github_link: ''
author: 'Ming Lee Ng'
tags:
  - LeetCode 100
  - Tree
  - Depth-First Search
  - Binary Tree
image: /images/blog/blog3.jpg
description: 'The Everyday Persons Guide to LeetCode #100'
toc:
socials:
---

## Introduction

Hello and welcome! I'm Ming Lee, and today we're going to cover **How to solve LeetCode 100 - Same Tree - in JS/TS :zap:**

Same as always we're gonna solve this, and we're gonna do it without the big fancy words because this is for regular folx! Keeping it nice and casual
round these parts! Movin' on...

## Problem

<b><a href='https://leetcode.com/problems/same-tree'>`LeetCode 100 - Same Tree`</a></b>

Given the roots of two binary trees p and q, write a function to check if they are the same or not.

Two binary trees are considered the same if they are structurally identical, and the nodes have the same value.

## Explanation

Ok, another Binary Tree problem. This one should be a little easier though! We're still using recursion, and we're just gonna check the values between
two TreeNodes. There are a couple of things we need to consider.

1. If both p AND q are null, then that's a good thing! That means they're the same! return true
2. If p OR q is null, then they can't be equal. One is null and one isn't. return false

After we handle the above base-cases we'll work on the "real" operations. We want to call isSameTree(p.left, q.left) to compare the left branches of
the trees, and we want to also call isSameTree(p.right, q.right). If either of those return false, we know that the trees aren't the same, so we
return false. That means we'll need to && them together. But we also need to check the current node, so lets && p.val === q.val as well to check and
see if the current q node is equal to the current p node. We'll return both function calls and the conditional all &&'d together.

## Solution

```
function isSameTree(p: TreeNode | null, q: TreeNode | null): boolean {
  if(!p && !q) return true;
  if(!p || !q) return false;

  return isSameTree(p.left, q.left) && p.val === q.val && isSameTree(p.right, q.right);
}
```

## Closing

Excellent! Hopefully everyone kept up! This was a really fun one for our first Binary Tree kind of problem! We'll be learning all kinds of ways to
traverse trees, but inorder is always a fun one! Our work with Binary Trees isn't over yet though, as our next problem is going to be
<a href='../symmetrictree'>**`LeetCode 101 - Symmetric Tree`**</a>! See you then!
