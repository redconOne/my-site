---
title: 'Implement Queue using Stacks'
date: 2023-01-19
draft: false
github_link: ''
author: 'Ming Lee Ng'
tags:
  - LeetCode 232
  - Stack
  - Queue
  - Design
image: /images/blog/blog3.jpg
description: 'The Everyday Persons Guide to LeetCode #232'
toc:
socials:
---

## Introduction

Hello and welcome! I'm Ming Lee, and today we're going to cover **How to solve LeetCode 232 - Implement Queue using Stacks - in JS/TS :zap:**

Same as always we're gonna solve this, and we're gonna do it without the big fancy words because this is for regular folx! Keeping it nice and casual
round these parts! Movin' on...

## Problem

<b><a href='https://leetcode.com/problems/implement-queue-using-stacks'>`LeetCode 232 - Implement Queue using Stacks`</a></b>

Implement a first in first out (FIFO) queue using only two stacks. The implemented queue should support all the functions of a normal queue (push,
peek, pop, and empty).

Implement the MyQueue class:

void push(int x) Pushes element x to the back of the queue. int pop() Removes the element from the front of the queue and returns it. int peek()
Returns the element at the front of the queue. boolean empty() Returns true if the queue is empty, false otherwise. Notes:

You must use only standard operations of a stack, which means only push to top, peek/pop from top, size, and is empty operations are valid. Depending
on your language, the stack may not be supported natively. You may simulate a stack using a list or deque (double-ended queue) as long as you use only
a stack's standard operations.

## Explanation

Ok, so we're going to plan on treating this problem similar to its little brother, <a href='../implementstackusingqueues/>Implement Stack using
Queues</a>. The major difference being that we need a stack, which is a LIFO data structure to be created using a queue, which is a LILO data
structure.

First things first, lets work on creating a MyStack class and constructor:

```
class MyStack {
  arr;
  size;
  constructor(){
    this.arr = [];
    this.size = 0;
  }
}
```

We also need to implement the other methods, push, pop, and peek. Because a stack is LIFO we will simply push and pop on the this.arr and peek will
just check the last element in the array.

```
push (val: number): void {
  this.arr.push(val);
  this.size++;
}

pop (): number | null {
  if (this.size < 1) return null;
  this.size--;
  return this.arr.pop();
}

peek (): number | null {
  if (this.size < 1) return null;
  return this.arr[this.size - 1];
}
```

Now that our stack is completely finished lets work on the queue. First of all, we need a stack to work with and a constructor, like this:

```
class MyQueue {
  stack;
  constructor () {
    this.stack = new MyStack();
  }
}
```

Then we need to work on the push method. Now, because this requires us to add the element to the start of the queue and stacks only add/pop from the
end we need to be careful about how we approach this. First thing we need to do is create a second, temporary stack. We then pop all the values from
this.stack into the temporary stack. Once all the values are added, we can push the value we want added to this.stack, and then pop all the values
from temp and push them back into this.stack. It sounds a little wild, but it looks like this:

```
push (val: number): void {
  const temp = new MyStack();
  while(this.stack.size) temp.push(this.stack.pop());
  this.stack.push(val);
  while(temp.size) this.stack.push(temp.pop());
}
```

Now that push is taken care of, things get really simple. Our peek just calls this.stack's peek because we handled all the heavy lifting in our push
method to make this work properly with a queue. Same thing for pop. It will also be handled by our MyStack class. We can handle empty pretty easily by
checking the this.stack.size value as well.

```
empty (): boolean {
  return this.stack.size < 1;
}
```

All in all the complete response to the problem should look a little like this:

## Solution

```
class MyStack {
  arr;
  size;
  constructor () {
    this.arr = [];
    this.size = 0;
  }

  push (val: number): void {
    this.size++;
    this.arr.push(val);
  }

  peek (): number | null {
    if (this.size < 1) return null;
    return this.arr[this.size - 1];
  }

  pop (): number | null {
    if (this.size < 1) return null;
    this.size--;
    return this.arr.pop();
  }
}

class MyQueue {
  stack;
  constructor () {
    this.stack = new MyStack();
  }

  push (val: number): void {
    const temp = new MyStack();
    while(this.stack.size) temp.push(this.stack.pop());
    this.stack.push(val);
    while(temp.size) this.stack.push(temp.pop());
  }

  peek (): number | null {
    return this.stack.peek();
  }

  pop (): number | null {
    return this.stack.pop();
  }

  empty (): boolean {
    return this.stack.size < 1;
  }
}
```

## Closing

And there you have it! We've now implemented a queue using stacks! I look forward to seeing everyone in the next one:
<a href='../palindromelinkedlist/'>**`LeetCode 234 - Palindrome Linked List`**</a>! See you then!
