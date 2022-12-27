---
title: 'Symmetric Tree'
date: 2022-12-23
draft: false
github_link: ''
author: 'Ming Lee Ng'
tags:
  - LeetCode 101
  - Tree
  - Depth-First-Search
  - Breadth-First-Search
  - Binary Tree
image: /images/blog/blog1.jpg
description: 'The Everyday Persons Guide to LeetCode #101'
toc:
socials:
---

## Introduction

Hello and welcome! I'm Ming Lee, and today we're going to cover **How to solve LeetCode 101 - Symmetric Tree - in JS/TS :zap:**

Same as always we're gonna solve this, and we're gonna do it without the big fancy words because this is for regular folx! Keeping it nice and casual
round these parts! Movin' on...

## Problem

<b><a href='https://leetcode.com/problems/symmetric-tree'>`LeetCode 101 - Symmetric Tree`</a></b>

Given the root of a binary tree, check whether it is a mirror of itself (i.e., symmetric around its center).

## Explanation

What a cool problem we have ahead of us! This one sounds pretty intimidating, but we're really just checking to see if the left and right branches of
root mirror each other. They have to be totally and completely identical, just mirrored. So while we can do this in one function, I really think that
I enjoy making a helper function for this one. Now what we're going to want to do is compare the root's left branch to the root's right branch. This
will require us to pass root.left and root.right into a helper function.

Now lets take a gander at this helper function. Lets start by saying its a function that takes in two parameters, (left and right), and returns a
boolean. We do have some base-case work to handle first and foremost as well.

1. So we know now that if left is null and right is null that the nodes are symmetrical because neither one exists! So if(!left && !right) return
   true;
2. We also know that if one of our args is null and the other isn't that the MUST be different, and we should return false. if(!left || !right) return
   false;

Now that's just our base case. We still have a lot more work to do. We also need to compare the current values. If left.val !== right.val we need to
return false;

The next step is where things get kind of funky. We need to check the left branch's left branch and compare it to the right branch's right branch. To
do this we'll call ourselves recursively by using helper(left.left, right.right). This will return a boolean. If its false, we need to return false.

The above step was just for comparing left's left with right's right. But we also need to compare left's right with right's left. (I know, it sounds
like madness, but hang in there). To do that comparison we need to do a helper(left.right, right.left). If its false, return false

Assuming we've made it through all of the checks above there can only be one answer left... its symmetrical! (at least at this current position) so we
return true!

Lets take a look at this code!

## Solution

```
function isSymmetric(root: TreeNode | null): boolean {
  return helper(root, root);
}

function helper(left: TreeNode | null, right: TreeNode | null): boolean {
  if(!left && !right) return true;
  if(!left || !right) return false;

  if(left.val !== right.val) return false;
  if(!helper(left.left, right.right)) return false;
  if(!helper(left.right, right.left)) return false;

  return true;
}
```

## Closing

Awesome! This is a pretty fun problem, and probably one of my favorites to re-visit. Keep in mind that there are multiple ways to implement this. You
can check all the way down the depth first in a depth-first-search, or you can check each node before you check its branches in a breadth-first-search
kind of manner. Neither is wrong, neither is right, and both had advantages and disadvantages. You could also && a lot of those booleans together for
a return. The choice is totally in your hands! Have fun with it, play around with it, and find out what code makes the most sense to you personally!
You've got this! Keep playing around with those binary trees though, because we'll be covering them much more in the super near future in the problem
<a href='../maximumdepthofbinarytree/'>**`LeetCode 104 - Maximum Depth of Binary Tree`**</a>!See you then!
