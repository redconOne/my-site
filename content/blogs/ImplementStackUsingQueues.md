---
title: 'Implement Stack using Queues'
date: 2023-01-15
draft: false
github_link: ''
author: 'Ming Lee Ng'
tags:
  - LeetCode 225
  - Stack
  - Design
  - Queue
image: /images/blog/blog2.jpg
description: 'The Everyday Persons Guide to LeetCode #225'
toc:
socials:
---

## Introduction

Hello and welcome! I'm Ming Lee, and today we're going to cover **How to solve LeetCode 225 - Implement Stack using Queues - in JS/TS :zap:**

Same as always we're gonna solve this, and we're gonna do it without the big fancy words because this is for regular folx! Keeping it nice and casual
round these parts! Movin' on...

## Problem

<b><a href='https://leetcode.com/problems/implement-stack-using-queues'>`LeetCode 225 - Implement Stack using Queues`</a></b>

Implement a list-in-first-out (LIFO) stack using only two queues. The implemented stack should support all the functions of a normal stack (push, top,
pop, and empty)

Implement the MyStack class:

- void push(int x) Pushes element x to the top of the stack.
- int pop() Removes the element on the top of the stack and returns it.
- int top() Returns the element on the top of the stack.
- boolean empty() Returns true if the stack is empty, false otherwise.

Notes:

- You must use only standard operations of a queue, which means that only push to back, peek/pop from front, size, and is empty operations are valid.
- Depending on your language, the queue may not be supported natively. You may simulate a queue using a list or deque (double-ended queue) as long as
  you use only a queue's standard operations.

## Explanation

Ok, so we're just creating a stack data structure using queues! This is definitely do-able. So queues are data structures where when you add to the
queue it adds at the end, and when you pop pops off the element at the front. Think of it as a line, like at the grocery store, where things are
Last-In-Last-Out(LILO). A stack is like a stack of pancakes. The last thing we added is going to be the next thing we eat! Last-In-First-Out (LIFO).
The first thing we need to do is create a new class for handling queues. Lets name it MyQueue! We should start it off looking something like this:

```
class MyQueue{
  queue;
  constructor() {
    this.queue = [];
  }
}
```

Ok, now lets handle some of the queue methods. We're gonna need to work on push, peek, pop, size, and isEmpty.

- push is straight forward. We just need to push to the queue array
- peek is always going to return whatever is at queue[0]
- pop returns a peek, but also does a queue.shift() operation
- size returns queue.length
- isEmpty returns a boolean of queue.length === 0 This looks like the following in code:

```
class MyQueue {
  queue;
  constructor(){
    this.queue = [];
  }
  push(n: number): void {
    this.queue.push(n);
  }
  peek(): number | null{
    return this.queue[0];
  }
  pop(): number | null {
    const r = this.peek();
    this.queue.shift();
    return r;
  }
  size(): number {
    return this.queue.length;
  }
  isEmpty(): boolean {
    return this.queue.length == 0;
  }
}
```

Now that we have our queues implemented, lets work on our MyStack. So lets have a look at what we need there. We need a MyQueue kind of object in
there, as well a constructor, push, pop, top, and empty. The constructor and the like should look something like the following:

```
class MyStack {
  q;
  constructor() {
    this.q = new MyQueue();
  }
}
```

From here when we work on the push() function we're going to take in a number, and we're not returning anything. So this operation is kind of funky.
We need to add a current value to the front of the queue, but we don't really have access to the front of the queue. So what we need to do is find the
length, then push our value. From there we need to store a pop a value from the queue, then push that value back to the end of the queue until the
value we just added is at the front of the queue. That means we would have to do that x amount of times, where x is the original length of the queue.
Sound funky? Well, it should look a little like the following, and hopefully that helps clear things up:

```
push(num: number): void{
  const len = this.q.size();
  this.q.push(num);
  for(let i = 0; i < l; ++i){
    const temp = this.q.pop();
    this.q.push(temp);
  }
}
```

Because we worked so hard on the push method pop() should be straight forward. We just return this.q.pop().

Top is similar. We just need to return this.q.peek().

Empty is going to be straightforward as well because we already have an isEmpty from queue. So return this.q.isEmpty()

Altogether both classes should look like the following:

## Solution

```
class MyQueue{
  queue
  constructor(){
    this.queue = [];
  }
  push(num: number): void {
    this.queue.push(num);
    console.log(this.queue)
  }
  peek(): number | null {
    return this.queue[0];
  }
  pop(): number | null {
    const temp = this.peek();
    this.queue.shift();
    return temp;
  }
  size(): number {
    return this.queue.length;
  }
  isEmpty(): boolean {
    return this.queue.length === 0;
  }
}

class MyStack {
  q
  constructor(){
    this.q = new MyQueue();
  }
  push(num: number): void {
    const len = this.q.size();
    this.q.push(num)
    for(let i = 0; i < len; ++i){
      const temp = this.q.pop();
      this.q.push(temp);
    }
  }
  pop(): number {
    return this.q.pop();
  }
  top(): number {
    return this.q.peek();
  }
  empty(): boolean {
    return this.q.isEmpty();
  }
}
```

## Closing

Pshew! This was a lengthy one, but it should have been fairly straight forward if you understand what you're doing with classes and understand how
queues/stacks work. This is really good practice moving forward and is another great leetcode problem to reference in the future for class/queue/stack
operations! Our next problem is going to be a super popular Binary Tree style problem -
<a href='../invertbinarytree/'>**`LeetCode 226 - Invert Binary Tree`**</a>! See you then!
