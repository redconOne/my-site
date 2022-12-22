---
title: 'Binary Tree Inorder Traversal'
date: 2022-12-21
draft: false
github_link: ''
author: 'Ming Lee Ng'
tags:
  - LeetCode 94
  - Stack
  - Tree
  - Depth-First Search
  - Binary Tree
image: /images/blog/blog2.jpg
description: 'The Everyday Persons Guide to LeetCode #94'
toc:
socials:
---

## Introduction

Hello and welcome! I'm Ming Lee, and today we're going to cover **How to solve LeetCode 94 - Binary Tree Inorder Traversal - in JS/TS :zap:**

Same as always we're gonna solve this, and we're gonna do it without the big fancy words because this is for regular folx! Keeping it nice and casual
round these parts! Movin' on...

## Problem

<b><a href='https://leetcode.com/problems/binary-tree-inorder-traversal'>`LeetCode 94 - Binary Tree Inorder Traversal`</a></b>

Given the root of a binary tree, return the inorder traversal of its node's values.

## Explanation

Ok, so first things first. We're dealing with Binary Trees, meaning that each Node is going to contain a node.left, node.right, and a node.val. Now we
want to access the values "in order" Meaning that we want to return an array containing all of the values of the Binary Tree. We want the .left values
to be first, then the current value, then the .right values. The easiest way to handle this is with recursion. Recursion is when a function calls
itself under certain circumstances.

Lets take a look at the first example. It looks something like this:

```
 1
  \
   2
  /
 3
```

So looking at our root node, the one containing the value 1 we need to add all of the root.left values to an array first. Since root.left is null,
there's nothing that we need to add! Easy! We'll handle that by checking to see if root is null. If so, we'll return an empty array. After the left
values are added, we'll add root.val. Then from there we'll add all the root.right values to the array, so we'll call inorderTraversal(root.left).
That will take us to node 2. Our array will currently look something like this [1], and we need to add node 2's .left values to it. So we'll call
inorderTraversal(root.left) and it will take us to node 3. Here at node 3 there is no .left, so we add .val to the array. The array is now [1,3].
There's no .right to add, so we just return the array back to node 2. Node 2 will add itself to the array resulting in [1,3,2]. There's no .right to
that node, so we return back to node 1 where we return the array [1,3,2].

That might sound a little complicated, but trust me, it makes a lot more sense when you see it code! Unfortunately its really difficult to explain
recursive functions via text, or tables, so you'll really just need to play around with it and experiment to get a better understanding of what's
going on.

## Solution

```
function inorderTraversal(root: TreeNode | null, arr: number[] = []): number[] {
  if(!root) return arr;

  inorderTraversal(root.left, arr);
  arr.push(root.val);
  inorderTraversal(root.right, arr);

  return arr;
}
```

## Closing

Excellent! Hopefully everyone kept up! This was a really fun one for our first Binary Tree kind of problem! We'll be learning all kinds of ways to
traverse trees, but inorder is always a fun one! Our work with Binary Trees isn't over yet though, as our next problem is going to be
<a href='../sametree/'>**`LeetCode 100 - Same Tree`**</a>! See you then!
