---
title: 'Binary Tree Postorder Traversal'
date: 2023-01-02
draft: false
github_link: ''
author: 'Ming Lee Ng'
tags:
  - LeetCode 145
  - Stack
  - Tree
  - Depth-First-Search
  - Binary Tree
image: /images/blog/blog2.jpg
description: 'The Everyday Persons Guide to LeetCode #145'
toc:
socials:
---

## Introduction

Hello and welcome! I'm Ming Lee, and today we're going to cover **How to solve LeetCode 145 - Binary Tree Postorder Traversal - in JS/TS :zap:**

Same as always we're gonna solve this, and we're gonna do it without the big fancy words because this is for regular folx! Keeping it nice and casual
round these parts! Movin' on...

## Problem

<b><a href='https://leetcode.com/problems/binary-tree-postorder-traversal'>`LeetCode 145 - Binary Tree Postorder Traversal`</a></b>

Given the root of a binary tree, return the postorder traversal of its nodes' values.

## Explanation

Alright, this one should feel really similar to the last problem we solved, the <b><a href='../binarytreepreordertraversal/'>Binary Tree Preorder
Traversal</a></b>. The main difference is that instead of adding each number BEFORE we call root.left and root.right we need to add it AFTER. Other
than that, the code should look super familiar!

Lets take a look at the example below and see how the postorder traversal should look.

```
     1
   /   \
  2     3
 / \   / \
4   5 6   7

```

The preorder of this tree should look like this [4,5,2,6,7,3,1]

We start at node 1 where we:

1. call function on root.left (2)
2. call function on root.right (3)
3. add 1 to arr

From there we hit node 2 where we:

1. call function on root.left (4)
2. call function on root.right (5)
3. arr 2 to arr

Then at node 4 we:

1. call function on root.left (null)
2. call function on root.right (null)
3. add 4 to arr

nulls do nothing

We go back to node 2's root.right call, aka node 5

1. call function on root.left (null)
2. call function on root.right (null)
3. add 5 to arr

And so on and so forth for the right side.

So looking at this we know that if we're passed null we need to just return outta there, otherwise we need to call ourselves recursively on its roots
left/right nodes and add root.val to arr.

The code for this should look something like the following

## Solution

```

function postorderTraversal(root: TreeNode | null, arr:number[] = []): number[] {
  if(!root) return [];

  postorderTraversal(root.left, arr);
  postorderTraversal(root.right, arr);
  arr.push(root.val);

  return arr;
};

```

## Closing

Nice! Super super close to what we had before, but that's just the nature of the problem! There are tons of ways to try and traverse a Binary Tree,
and these are two really fun ways to gather up all the values inside. As with most of these data structures, try and familiarize yourself with them as
we'll definitely be seeing them again in the future. Speaking of data structures, our next problem is going to involved Linked Lists, so prepare for
those for the problem <a href='../intersectionoftwolinkedlists/'>**`LeetCode 160 - Intersection of Two Linked Lists`**</a>! See you then!
