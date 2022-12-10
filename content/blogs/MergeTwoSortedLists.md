---
title: 'Merge Two Sorted Lists'
date: 2022-12-10
draft: false
github_link: ''
author: 'Ming Lee Ng'
tags:
  - LeetCode 21
  - Merge Two Sorted Lists
  - Linked List
  - Recursion
image: /images/blog/blog3.jpg
description: 'The Everyday Persons Guide to LeetCode #21'
toc:
socials:
---

## Introduction

Hello and welcome! I'm Ming Lee, and today we're going to cover **How to solve
LeetCode 21 - Merge Two Sorted Lists - in JS/TS :zap:**

Same as always we're gonna solve this, and we're gonna do it without the big
fancy words because this is for regular folx! Keeping it nice and casual round
these parts! Movin' on...

## Problem

<b><a href='https://leetcode.com/problems/merge-two-sorted-lists'>`LeetCode 21 - Merge Two Sorted Lists`</a></b>

You are given the heads of two sorted linked lists list1 and list2.

Merge the two lists in a one sorted list. The list should be made by splicing
together the nodes of the first two lists.

Return the head of the merged linked list.

## Explanation

Ok, so to start we're gonna need to know what Linked Lists are. Linked Lists are
a type of data structure that typically point from 1 object to its "next" in a
chain. We tend to hold onto the head of the linked list, like a snake, and we
can check down the list for data we need by doing some .next action. Most linked
lists do not store the size, and in the typical linked list you cannot look at a
previous element either. They typically are just objects with a .val which
stores a number or string, and a .next that is a pointer to the next node in the
linked list.

Ok. Now that that's out of the way, lets consider what we're looking at here. We
want to return both of these linked lists combined, so the first thing we want
to do is create a new head pointer to hold onto. Lets name this something like
newHead, and we'll make it a completely blank listnode with no value and no
next. It should look something like this const newHead = new ListNode(); We also
need something to hold on to our current location within our new Linked List.
Lets name this current, and it will be set to newHead. const current = newHead.
Now when we're creating out Linked List we can use current to go through and
populate the values while newHead just sits there and looks pretty. At the end
of it all we then return newHead.next, which will return the first ListNode in
our Linked List.

Now to create our Linked List. We want to continue doing some kind of comparison
while list1 has length and list2 has length. But there is no .length or .size
for Linked Lists. So instead we'll do something like while(list1 && list2). Once
we're in the while loop we want to compare list1.val to list2.val and set
current.next to the one with the lowest value. Once current.next is set to that
particular ListNode, we'll advance that List. Lets say that list1 has the lowest
value. Then we want to do current.next = list1 immediately followed by list1 =
list1.next to advance it to the next position. Then, regardless of whether we
used a list1 element or a list2 element, we need current to advance to
current.next.

Now once we've exited the while loop either list1 or list2 is null. But the
other list likely contains values, and we need those values. So we'll just
assigned current.next to whichever list still contains values.

The last step, as we mentioned earlier, is to return newHead.next in order to
return our new sorted linked list. All in all it should look something like the
following.

## Solution

```
const mergeTwoLists = (list1: ListNode | null, list2: ListNode | null): ListNode | null => {
  const newHead = new ListNode();
  let current = newHead;

  while(list1 && list2){
      if(list1.val <= list2.val){
          current.next = list1;
          list1 = list1.next;
      } else {
          current.next = list2;
          list2 = list2.next;
      }

      current = current.next;
  }

  if(list1) current.next = list1;
  if(list2) current.next = list2;

  return newHead.next;
};
```

## Closing

Great work! This one may have felt kind of rough for those of us that have never
seen Linked Lists. Don't worry though, they're not as bad as they seem at first!
Linked Lists are really fun to work with, and a super simple data structure to
understand once you get the hand of them. Its important to really get the hand
of working with different types of data structures, and can really help expand
your thinking and problem-solving capabilities. I highly encourage everyone to
keep practicing and don't avoid these types of problems, even if they seem a
little out of the ordinary. You've got this! Our next problem is going to be a
little calmer as we're looking into finding a solution for
<a href='../removeduplicatesfromsortedarray/'>**`LeetCode 26 - Remove Duplicates from Sorted Array`**</a>!
See you then!
