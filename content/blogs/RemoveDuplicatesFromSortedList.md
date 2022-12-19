---
title: 'Remove Duplicates From Sorted List'
date: 2022-12-19
draft: false
github_link: ''
author: 'Ming Lee Ng'
tags:
  - LeetCode 83
  - Linked List
image: /images/blog/blog3.jpg
description: 'The Everyday Persons Guide to LeetCode #83'
toc:
socials:
---

## Introduction

Hello and welcome! I'm Ming Lee, and today we're going to cover **How to solve LeetCode 83 - Remove Duplicates from Sorted List - in JS/TS :zap:**

Same as always we're gonna solve this, and we're gonna do it without the big fancy words because this is for regular folx! Keeping it nice and casual
round these parts! Movin' on...

## Problem

<b><a href='https://leetcode.com/problems/remove-duplicates-from-sorted-list'>`LeetCode 83 - Remove Duplicates from Sorted List`</a></b>

Given the head of a sorted linked list, delete all duplicates such that each element appears only once. Return the linked list sorted as well.

## Explanation

Now this one is going to be a bit easier than it sounds at first. Because the list is already sorted we don't have to worry about the last sentence
where it tells us to return the list sorted. So all we really need to do is check each element of the linked list and compare it to its next value. If
those values are the same then the current node's .next needs to be pushed a little further. So we'll set current.next = current.next.next. That will
cut the duplicate right out of the linked list. The code should look a little something like the following:

## Solution

```
function deleteDuplicates(head: ListNode | null): ListNode | null {
  if(!head) return head;

  let current: ListNode = head;

  while(current.next)
    if(current.val === current.next.val)
      current.next = current.next.next;
    else
      current = current.next;

  return head;
}
```

## Closing

Good job! I hope everyone managed to keep up on this one! Linked Lists are a really fun data structure to learn how to wrangle and they're really cool
once you learn how to use them properly. This is a great problem to come back to later if you're feeling uncomfortable with Linked Lists, so make sure
to keep it in mind when it comes to practicing! Next on the list (haha) will be
<a href='../mergesortedarray/'>**`LeetCode 88 - Merge Sorted Array`**</a>! See you then!
