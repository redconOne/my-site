---
title: 'Path Sum'
date: 2022-12-20
draft: false
github_link: ''
author: 'Ming Lee Ng'
tags:
  - LeetCode 112
  - Tree
  - Depth-First-Search
  - Breadth-First-Search
  - Binary Tree
image: /images/blog/blog3.jpg
description: 'The Everyday Persons Guide to LeetCode #112'
toc:
socials:
---

## Introduction

Hello and welcome! I'm Ming Lee, and today we're going to cover **How to solve LeetCode 112 - Path Sum - in JS/TS :zap:**

Same as always we're gonna solve this, and we're gonna do it without the big fancy words because this is for regular folx! Keeping it nice and casual
round these parts! Movin' on...

## Problem

<b><a href='https://leetcode.com/problems/path-sum'>`LeetCode 112 - Path Sum`</a></b>

Given the root of a binary tree and an integer targetSum, return true if the tree has a root-to-leaf path such that adding up all the values along the
path equals targetSum.

A leaf is a node with no children.

## Explanation

Alrighty folx, this is gonna be our last Binary Tree problem for a short while, so hang in there! This is a pretty darn fun one where we're going to
need to consider how we want to navigate a Binary Tree, and how we want to find this targetSum. One super super important thing to remember here is
that we're specifically looking for a leaf. That means that we're looking for one of the ends to these branches where is has a value, but its .left
and .right are set to null.

So as always with Binary Trees we're going to want to consider a base case where we can bounce back. In this case, because we're dealing with
booleans, if root is null we want to return false. I'll probably implement this in something like if(!root) return false;

Assuming we've made it past the base case we can check to see if this is our target node! We can do that by checking if root.val === targetSum AND
!root.left AND !root.right. Remember, if it has a left or a right, its not a leaf, and we're specifically looking for leaves. If we meet the above
conditions, we return true!

If this isn't the node we're looking for we can continue onwards with some recursion. We can check the left branches with a hasPathSum(root.left,
targetSum - root.val) and check the right path with similar, just with root.right. Its important to notice that we're taking root.val from targetSum.
This allows us to account for the current node and ensure that its 'factored in' along the way.

Once we've checked the left and the right branches we just need to return if either of them are true.

## Solution

```
function hasPathSum(root: TreeNode | null, targetSum: number): boolean {
  if(!root) return false;

  if(root.val === targetSum && !root.left && !root.right) return true;

  return hasPathSum(root.left, targetSum - root.val) || hasPathSum(root.right, targetSum - root.val);
}
```

## Closing

Awesome! That's our it for Binary Trees for a few days, so you can let that sigh of relief out now! But don't get **too** relaxed as we're looking to
handle some mathy problems in the future by solving <a href='../pascalstriangle/'>**`LeetCode 118 - Pascal's Triangle`**</a>!See you then!
