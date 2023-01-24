---
title: 'Binary Tree Paths'
date: 2023-01-22
draft: false
github_link: ''
author: 'Ming Lee Ng'
tags:
  - LeetCode 257
  - String
  - Backtracking
  - Tree
  - Depth-First Search
  - Binary Tree
image: /images/blog/blog3.jpg
description: 'The Everyday Persons Guide to LeetCode #257'
toc:
socials:
---

## Introduction

Hello and welcome! I'm Ming Lee, and today we're going to cover **How to solve LeetCode 257 - Binary Tree Paths - in JS/TS :zap:**

Same as always we're gonna solve this, and we're gonna do it without the big fancy words because this is for regular folx! Keeping it nice and casual
round these parts! Movin' on...

## Problem

<b><a href='https://leetcode.com/problems/binary-tree-paths'>`LeetCode 257 - Binary Tree Paths`</a></b>

Given the root of a binary tree, return all root-to-leaf paths in any order.

A leaf is a node with no children.

## Explanation

Ok, so we know that in this one if the node is a leaf it has no children. If it has no children there are no paths that need to be written or
adjusted, we simply need to return that node's value up to its parent nodes. We can handle that like this

```
if(!root.left && !root.right) return [root.val.toString()];
```

Our other base case is that if root is null we need to return an empty array, like this:

```
if(!root) return [];
```

Now from here we only have one more part to work on, the actual building of the paths. So lets take a look at the left path first. We would
recursively call binaryTreePaths(root.left) and we want to map the result and add our current location to it every time, something like this:

```
const left = binaryTreePaths(root.left).map(path => `${root.val}->${path});
```

We would then need to do something similar on the right path. But since we need to combine left and right together to return as a result and they both
get mapped, we'll just handle that in one step. Maybe something like this:

```
const left = binaryTreePaths(root.left);
const right = binaryTreePaths(root.right);
return left.concat(right).map(path => `${root.val}->${path});
```

All in all our total solution should look a little something like the following.

## Solution

```
function binaryTreePaths(root: TreeNode | null): string[] {
  if (!root) return [];
  if (!root.left && !root.right) return [root.val.toString()];

  const left = binaryTreePaths(root.left);
  const right = binaryTreePaths(root.right);

  return left.concat(right).map(path => `${root.val}->{path});
}
```

## Closing

Great job! This one is a little funky but should really help solidify how we target leaves and how we are about to generate paths. We'll be looking
into some more recursion tomorrow in <a href='../adddigits/'>**`LeetCode 258 - Add Digits`**</a>! See you then!
