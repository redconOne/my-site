---
title: 'Binary Tree Preorder Traversal'
date: 2023-01-01
draft: false
github_link: ''
author: 'Ming Lee Ng'
tags:
  - LeetCode 144
  - Stack
  - Tree
  - Depth-First-Search
  - Binary Tree
image: /images/blog/blog1.jpg
description: 'The Everyday Persons Guide to LeetCode #144'
toc:
socials:
---

## Introduction

Hello and welcome! I'm Ming Lee, and today we're going to cover **How to solve LeetCode 144 - Binary Tree Preorder Traversal - in JS/TS :zap:**

Same as always we're gonna solve this, and we're gonna do it without the big fancy words because this is for regular folx! Keeping it nice and casual
round these parts! Movin' on...

## Problem

<b><a href='https://leetcode.com/problems/binary-tree-preorder-traversal'>`LeetCode 144 - Binary Tree Preorder Traversal`</a></b>

Given the root of a binary tree, return the preorder traversal of its nodes' values.

## Explanation

Yay! More Binary Trees! This one isn't asking for anything too crazy once you get down to it, so that's really lovely for us! We need to visit each
and every single node and add the value into an array. The problem is, the array needs to be sorted in a particular way, or rather, we need to visit
each node in a particular order.

So first lets take a look at 'preorder' This is just a fancy way of saying that we need to check the value, then call our function on root.left and
root.right. So if we have the following tree

```
     1
   /   \
  2     3
 / \   / \
4   5 6   7

```

The preorder of this tree should look like this [1,2,4,5,3,6,7]

We start at node 1 where we:

1. add 1 to arr
2. call function on root.left (2)
3. call function on root.right (3)

From there we hit node 2 where we:

1. add 2 to arr
2. call function on root.left (4)
3. call function on root.right (5)

Then at node 4 we:

1. add 4 to arr
2. call function on root.left (null)
3. call function on root.right (null)

nulls do nothing

We go back to node 2's root.right call, aka node 5

1. add 5 to arr
2. call function on root.left (null)
3. call function on root.right (null)

And so on and so forth for the right side.

So looking at this we know that if we're passed null we need to just return outta there, otherwise we need to push to an array and call root on its
left/right nodes.

The code for this should look something like the following

## Solution

```

function preorderTraversal(root: TreeNode | null, arr: number[] = []): number[] {
  if (!root) return [];

  arr.push(root.val);
  preorderTraversal(root.left, arr);
  preorderTraversal(root.right, arr);

  return arr;
}

```

## Closing

Whoo! I love seeing some short and sweet recursive functions! Here we're handling that base case of root being null by just returning an empty array.
Nothing catches that or anything, it just returns to the void. If root isn't null then we push values into arr, then call ourselves recursively. I
also took the liberty of setting arr to an empty array in the case its undefined, such as during the first call, that way we always have some kind of
array to work with. Keep in mind that we're passing an array down into the recursive functions and the push method is mutating this array, so we don't
need to do any kind of arr = preorderTraversal() stuff. We just call the function, let it do its thing, and then its done! Great job! Next time we'll
be heading right back into Linked Lists again as we handle
<a href='../intersectionoftwolinkedlists/'>**`LeetCode 160 - Intersection of Two Linked Lists`**</a>! See you then!
