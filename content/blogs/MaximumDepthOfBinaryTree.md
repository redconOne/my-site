---
title: 'Maximum Depth of Binary Tree'
date: 2022-12-24
draft: false
github_link: ''
author: 'Ming Lee Ng'
tags:
  - LeetCode 104
  - Tree
  - Depth-First-Search
  - Breadth-First-Search
  - Binary Tree
image: /images/blog/blog2.jpg
description: 'The Everyday Persons Guide to LeetCode #104'
toc:
socials:
---

## Introduction

Hello and welcome! I'm Ming Lee, and today we're going to cover **How to solve LeetCode 104 - Maximum Depth of Binary Tree - in JS/TS :zap:**

Same as always we're gonna solve this, and we're gonna do it without the big fancy words because this is for regular folx! Keeping it nice and casual
round these parts! Movin' on...

## Problem

<b><a href='https://leetcode.com/problems/maximum-depth-of-binary-tree'>`LeetCode 104 - Maximum Depth of Binary Tree`</a></b>

Given the root of a binary tree, return its maximum depth. A binary tree's maximum depth is the number of nodes along the longest path from the root
node down to the farthest leaf node.

## Explanation

Here we are again, battling the dreaded Binary Trees! But don't worry, a lot of the skills that we've picked up along the way are going to help us
feel a little more at home on this problem! The wording on this problem, like it is on most of these, is a little too fancy pants for me to understand
what they're asking for at a glance, so let's break it down a little.

What we're looking for is the furthest node away from the initial root node. So it could be down root.left or root.right, but we need to keep on
travelling down until we find the deepest node in the darkest dungeon. So with that in mind we can consider using a recursive function to travel down
all these funky branches on our tree.

So for a base case we need to consider what happens when root is null. Well, in that case we need to return the number 0. That will look something
like this if(!root) return 0

If root ISN'T null, we need to check its left and right branches. We can do that recursively! So we'll call our function on root.left and then
root.right. If it returns a number, we need to compare those numbers. If left is larger than right, we will return the left number + 1, else we'll
return right + 1. We return with a + 1 to account for the node that we're currently at.

## Solution

```
function maxDepth (root: TreeNode | null): number {
  if(!root) return 0;

  const left = maxDepth(root.left);
  const right = maxDepth(root.right);

  return left > right ? left + 1 : right + 1;
}
```

## Closing

Easy as that! We're working with more and more recursion as we deal with all these trees, so if it doesn't make sense yet keep working on those trees!
Recursion is one of those things that is really scary right up until it isn't. Once you really wrap your head around it recursion will turn from
something confusing and nightmareish to a super strong tool in your toolbelt! We have just a few more binary tree problems coming up before we get a
short break from them, so hang in there as we prepare to tackle our next tree problem in <a href='../pathsum/'>**`LeetCode 112 - Path Sum`**</a>!See
you then!
