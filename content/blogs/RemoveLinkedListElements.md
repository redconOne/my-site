---
title: 'Remove Linked List Elements'
date: 2023-01-10
draft: false
github_link: ''
author: 'Ming Lee Ng'
tags:
  - LeetCode 203
  - Linked List
  - Recursion
image: /images/blog/blog3.jpg
description: 'The Everyday Persons Guide to LeetCode #203'
toc:
socials:
---

## Introduction

Hello and welcome! I'm Ming Lee, and today we're going to cover **How to solve LeetCode 203 - Remove Linked List Elements - in JS/TS :zap:**

Same as always we're gonna solve this, and we're gonna do it without the big fancy words because this is for regular folx! Keeping it nice and casual
round these parts! Movin' on...

## Problem

<b><a href='https://leetcode.com/problems/remove-linked-list-elements'>`LeetCode 203 - Remove Linked List Elements`</a></b>

Given the head of a linked list and an integer val, remove all the nodes of the linked list that has Node.val === val, and return the new head.

## Explanation

Ok, so in this problem we are given a linked list and an element that needs to be removed. we need to make sure and remove all occurences of that
number from the linked list.

So to start, if the linked list that we're given is null, we can just return that null right back at em.

From there we can create a current ListNode to iterate through the Linked List that way we can continue holding onto the head to return later.

The next step is going to be us iterating through the entire list, while current and current.next are not null. During this loop we're going to want
to check current.next.val. If that value is the number that we wantto skip we need to do current.next = current.next.next otherwise we can go ahead
and advance current with current = current.next. This continues through the entire while loop until we've verified every single position.

The problem with all of the above is that the head element is never checked. The rest of the list is completely free of the target value, but the head
may still contain it. So if head.val === val we need to return head.next. Otherwise return head. Sounds a little wild? Clear as mud? Let's see if
actually seeing the code clears things up any.

## Solution

```
function removeElements(head: ListNode | null, val: number): ListNode | null {
  if(!head) return null;

  let current: ListNode | null = head;

  while(current && current.next)
    current.next.val === val ? current.next = current.next.next : current = current.next;

  return head.val === val ? head.next : head;
}
```

## Closing

That's another Linked List problem down! If this is giving you a little trouble I'd highly recommend giving it some more attention until Linked Lists
start making a little more sense to you. This is a great problem to help become more acquainted with Linked Lists, so keep at it until it starts to
feel a little more comfortable. You've got this! Tomorrow we're gonna tackle a fun dictionary type problem in
<a href='../isomorphicstrings/'>**`LeetCode 205 - Isomorphic Strings`**</a>! See you then!
