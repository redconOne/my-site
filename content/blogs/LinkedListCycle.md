---
title: 'Linked List Cycle'
date: 2022-12-31
draft: false
github_link: ''
author: 'Ming Lee Ng'
tags:
  - LeetCode 141
  - Hash Table
  - Linked List
  - Two Pointers
image: /images/blog/blog3.jpg
description: 'The Everyday Persons Guide to LeetCode #141'
toc:
socials:
---

## Introduction

Hello and welcome! I'm Ming Lee, and today we're going to cover **How to solve LeetCode 141 - Linked List Cycle - in JS/TS :zap:**

Same as always we're gonna solve this, and we're gonna do it without the big fancy words because this is for regular folx! Keeping it nice and casual
round these parts! Movin' on...

## Problem

<b><a href='https://leetcode.com/problems/linked-list-cycle'>`LeetCode 141 - Linked List Cycle`</a></b>

Given head, the head of a linked list, determine if the linked list has a cycle in it.

There is a cycle in a linked list if there is some node in the list that can be reached again by continuously following the next pointer. Internally,
pos is used to denote the index of the node that tail's next pointer is connected to. Note that pos is not passed as a parameter.

Return true if there is a cycle in the linked list. Otherwise return false.

## Explanation

What a gorgeous problem this is! So here we're wanting to see if there is a cycle in this linked list, or rather, if at some point any node in this
list links back to another node in the list. Sounds a little intimidating to figure out, but its actually not that bad!

Now, for the regular joe kind of solution you could easily look at this and think hey, why don't I just store all the visited nodes in an array or a
map or something and iterate node by node checking to see if we have that node in the array/map? That's a fine way of doing things, and definitely
works. But this problem does request that we try and find a way to do this with constant memory, and boy is there a way to make that happen!

So first of all, we know that we need to continue iterating through this linked list. If at any point the pointer that we're using is pointing to null
then there must not be a cycle, because we've ran out of nodes! That's something to consider. But that doesn't tell us how to stop if its a cycle
though. So how can we check and see if we've been somewhere without using linear memory? Well, to answer that we'll use a second pointer.

So we create a 'fast' pointer that is going to move from its current location to its .next.next, and we're going to have a 'slow' pointer that moves
from current location to .next So fast is actually moving twice as quickly through the linked list as slow. If at any point fast === null, then we
know that there is no cycle, but if at any point fast === slow then we know it must have found a cycle, circled back, and is now 'lapping' slow,
proving that there is a cycle.

So armed with this knowledge we can create some super fun code that should look something like this:

## Solution

```
function hasCycle(head: ListNode | null): boolean {
  let fast = head;
  let slow = head;

  while (fast && fast.next) {
    fast = fast.next.next;
    slow = slow?.next || null;

    if (fast === slow) return true;
  }

  return false;
};

```

## Closing

Sweet! This is a great way of telling if there is a cycle in a linked list, and is actually something that can come in handy when dealing with Linked
Lists. This isn't the last time that we'll see something like this, so try and familiarize yourself with how this works. Just remember, if there's a
cycle (if it loops back on itself), the Linked List is going to make a kind of circle, and our two pointers are eventually going to end up racing one
another, with our fast pointer moving twice as fast and eventually catching back up to our slow. Tomorrow we're going to encounter some Binary Trees,
so get prepared for that when we take a look at <a href='../binarytreepreordertraversal/'>**`LeetCode 144 - Binary Tree Preorder Traversal`**</a>! See
you then!
