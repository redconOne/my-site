---
title: 'Intersection of Two Linked Lists'
date: 2023-01-03
draft: false
github_link: ''
author: 'Ming Lee Ng'
tags:
  - LeetCode 160
  - Hash Table
  - Linked List
  - Two Pointers
image: /images/blog/blog3.jpg
description: 'The Everyday Persons Guide to LeetCode #160'
toc:
socials:
---

## Introduction

Hello and welcome! I'm Ming Lee, and today we're going to cover **How to solve LeetCode 160 - Intersection of Two Linked Lists - in JS/TS :zap:**

Same as always we're gonna solve this, and we're gonna do it without the big fancy words because this is for regular folx! Keeping it nice and casual
round these parts! Movin' on...

## Problem

<b><a href='https://leetcode.com/problems/intersection-of-two-linked-lists'>`LeetCode 160 - Intersection of Two Linked Lists`</a></b>

Given the heads of two singly linked-lists headA and headB, return the node at which the two lists intersect. If the two linked lists have no
intersection at all, return null.

## Explanation

Ok, so this one is a little complicated, but super fun. It does ask for us to try and make things linear in time complexity and constant in space
complexity, so we'll work on handling that. So lets take a look at the first example which should look a little something like this:

```
      a1 -- a2
              \
               c1 -- c2 -- c3
              /
b1 -- b2 -- b3
```

In this example we're looking at two linked lists, A and B, and they meet at position C1. So how can we tell that they meet? Well, we could keep an
array of nodes and check, that's certainly one way to handle things, but that isn't constant in memory use. Another way would be for us to force them
to be the same length, and then once they are the same length iterate through both the linked lists, checking both nodes. If node A === node B then we
know that they are intersecting. If they end up at null then we know that they never intersected.

So looking at our example, the first thing we need to do is find out the length of each list. Sounds good. In the example A has a length of 5 and B
has a length of 6. So we need to move headB forward to headB.next . After that A and B will both be of length 5. headA is A1 and headB is b2, so headA
!== headB. So in this case we move them both forward. headA is now a2 and headB is now b3, and they are not equal, so we advance them both again. Now
headA is c1 and headB is c1. They are the same, and thus intersected. Lets take a look at this in code.

## Solution

```

function getIntersectionNode(headA: ListNode | null, headB: ListNode | null): ListNode | null {
  let lengthA = 0;
  let lengthB = 0;

  let tempA = headA;
  let tempB = headB;

  // finding the length of headA's list
  while (tempA) {
    tempA = tempA.next;
    lengthA++;
  }
  // finding the length of headB's list
  while (tempB) {
    tempB = tempB.next;
    lengthB++;
  }

  // find the difference. If diff is > 0 list A is larger. Else list B is larger.
  let diff = lengthA - lengthB;

  // making the lists of equal length
  while (diff !== 0) {
    if (diff > 0) {
      headA = headA?.next || null;
      diff--;
    } else {
      headB = headB?.next || null;
      diff++;
    }
  }

  while (headA !== headB) {
    headA = headA?.next || null;
    headB = headB?.next || null;
  }

  return headA;
}

```

## Closing

Whoo! That one was a little bit of a wild one! I tried to include some comments in the code to help out a bit. Its also totally reasonable to include
a helper function so you don't have to rewrite a lot of this code. Now before everyone comes out, pushes up their glasses and starts with the "well
akshually" nonsense, yes, I know that we can solve this with two pointers moving through the lists, comparing to each other and setting to the others
start if one is null, but that's a little excessive for this particular problem, so don't get riled up over it. We'll be taking a bit of a break from
data structures and looking into the wonderful world of excel spreadsheets tomorrow by solving
<a href='../excelsheetcolumntitle/'>**`LeetCode 168 - Excel Sheet Column Title`**</a>! See you then!
