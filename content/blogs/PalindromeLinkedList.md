---
title: 'Palidrome Linked List'
date: 2023-01-20
draft: false
github_link: ''
author: 'Ming Lee Ng'
tags:
  - LeetCode 234
  - Linked List
  - Two Pointers
  - Stack
  - Recursion
  - Queue
image: /images/blog/blog1.jpg
description: 'The Everyday Persons Guide to LeetCode #234'
toc:
socials:
---

## Introduction

Hello and welcome! I'm Ming Lee, and today we're going to cover **How to solve LeetCode 234 - Palidrome Linked List - in JS/TS :zap:**

Same as always we're gonna solve this, and we're gonna do it without the big fancy words because this is for regular folx! Keeping it nice and casual
round these parts! Movin' on...

## Problem

<b><a href='https://leetcode.com/problems/palindrome-linked-list'>`LeetCode 234 - Palidrome Linked List`</a></b>

Given the head of a singly linked list, return true if it is a palindrome or false otherwise.

## Explanation

Ok, so this one is a fun linked list kind of problem. So we want to know if a linked list traversed from head -> tail is the same as the same linked
list from tail -> head. Because linked lists only have a .next and not a .previous we're going to have to reverse our list. Once we have a reversed
linked list we can compare it to our original linked list and verify that they are the same, node by node.

So to begin with creating a new linked list we need to create two new nodes. One to help us navigate the list and one to store the reversed list.

```
let current = head;
let reverse = null;
```

From there we want to navigate the entire linked list and make sure that reverse is populated as we go. We need to make a pointer to hold on to
reverse's node, then set reverse to a new ListNode, where the .val = current.val and its .next is the temporary pointer. One that's done we'll advance
current. It should look a little like this:

```
while (currrent) {
  const temp = reverse;
  reverse = new ListNode(current.val, temp);
  current = current.next;
}
```

Now that we have the reversed list let's start our comparison. From here we need to iterate while head and reverse are not null. During the iteration
if head.val is different from reverse.val we return false. Otherwise we advance head and reverse to their respective .nexts like so:

```
while (head && reverse) {
  if (head.val !== reverse.val) return false;
  head = head.next;
  reverse = reverse.next;
}
```

After the while loop both head and reverse should be false. So we can just return !head and !reverse together. All in all everything should look a
little like this:

## Solution

```
function isPalindrome(head: ListNode | null): boolean {
  let current = head;
  let reverse = null;

  while(current) {
    const temp = reverse;
    reverse = new ListNode(current.val, temp);
    current = current.next;
  }

  while(reverse && head) {
    if(reverse.val !== head.val) return false;
    reverse = reverse.next;
    head = head.next;
  }

  return !reverse && !head;
}
```

## Closing

Great work! This one combined a few other problems into one! For those of you that remember <a href='../reverselinkedlist/'>Reverse Linked List </a>
this one might have felt a little easier. Next we'll be tackling <a href='../validanagram/'>**`LeetCode 242 - Valid Anagram`**</a>! See you then!
