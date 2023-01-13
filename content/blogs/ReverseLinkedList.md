---
title: 'Reverse Linked List'
date: 2023-01-12
draft: false
github_link: ''
author: 'Ming Lee Ng'
tags:
  - LeetCode 206
  - Linked List
  - Recursion
image: /images/blog/blog2.jpg
description: 'The Everyday Persons Guide to LeetCode #206'
toc:
socials:
---

## Introduction

Hello and welcome! I'm Ming Lee, and today we're going to cover **How to solve LeetCode 206 - Reverse Linked List - in JS/TS :zap:**

Same as always we're gonna solve this, and we're gonna do it without the big fancy words because this is for regular folx! Keeping it nice and casual
round these parts! Movin' on...

## Problem

<b><a href='https://leetcode.com/problems/reverse-linked-list'>`LeetCode 206 - Reverse Linked List`</a></b>

Given the head of a singly linked list, reverse the list, and return the reversed list.

## Explanation

Ok, so this one is a little funky. It sounds really simple to just reverse a linked list, and if we want to handle this with something like an array,
it really is pretty simple, but to handle this without an array using constant memory requires a little bit of thinking. I'd like to approach this
looking at the first example where the list is 1 -> 2 -> 3 -> 4 -> 5 let's try and reverse it.

First things first, we have the head pointer already, so we'll keep using that, but we need to make a new "tail" for head to start reversing with.
Let's name it previous and set it to null.

At this point we have:

```
previous = null
head = 1 -> 2 -> 3 -> 4 -> 5 -> null
```

So from here we need to implement a while loop. This loop is going to continue for a long as head is not null. Inside the loop we're going to do some
fun operations.

1. create a temp variable to hold head.next.
2. set head.next to previous
3. set previous to head
4. set head to temp

So after the first iteration in the while we have something like this:

```
previous = 1 -> null
head = 2 -> 3 -> 4 -> 5 -> null
```

After the second iteration we have this:

```
previous = 2 -> 1 -> null
head = 3 -> 4 -> 5 -> null
```

This is going to continue all the way until head is null, which will look something like this:

```
previous = 5 -> 4 -> 3 -> 2 -> 1 -> null
head = null
```

At this point we simply return previous and we're done!

## Solution

```
function reverseList(head: ListNode | null): ListNode | null {
  let previous = null;

  while(head){
    const temp = head.next;
    head.next = previous;
    previous = head;
    head = temp;
  }

  return previous;
}
```

## Closing

Wow! What a wild problem! This is one of those problems that is super cool to solve! Just make sure you're always keeping track of your pointers and
not dropping any data and you're good to go! I look forward to seeing everyone in the next problem, which is
<a href='../containsduplicate/'>**`LeetCode 217 - Contains Duplicate`**</a>! See you then!
