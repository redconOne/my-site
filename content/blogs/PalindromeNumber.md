---
title: 'Palindrome Number'
date: 2022-12-06
draft: false
github_link: ''
author: 'Ming Lee Ng'
tags:
  - LeetCode 9
  - Palindrome Number
  - String Methods
image:
description: 'The Everyday Persons Guide to LeetCode #9'
toc:
socials:
---

## Introduction

Hello and welcome! I'm Ming Lee, and today we're going to cover **How to solve
LeetCode 9 - Palindrome Number - in JS/TS :zap:**

Same as always we're gonna solve this, and we're gonna do it without the big
fancy words because this is for regular folx! Keeping it nice and casual round
these parts! Movin' on...

## Problem

<b><a href='https://leetcode.com/problems/palindrome-number'>`LeetCode 9 - Palindrome Number`</a></b>

Given an integer **x**, return **true** if **x** is a palindrome, and **false**
otherwise.

## Important Keywords

Palindrome : a word (or number) that is the same both forwards and backwards

## Explanation

Nice! So this is a test of "do you know your JavaScript methods"? Now array's
have a really neat .reverse() method, and we'd love to use that, but sadly
numbers don't have access to that. Strings can split() into an array though, and
we can always .toString() numbers into strings, so that's our plan of action on
how to gain access! Once we can reverse the number we want to turn it back into
a number from its reversed array counterpart and compare that to the original.
So the steps should look something like this:

1. Do a .toString() on a number to get the string version
2. Do a .split('') on that string to get an array
3. Perform the .reverse()! :zap:
4. Do a .join('') to return to a string
5. Cast the string back into a number with either + or Number()

As always, this will be done in TypeScript, but all my JS folx don't be
discouraged, this should be totally readable! Try and ignore all the colons and
the types that follow them. The code should look super familiar if you can get
past that!

## Solution

```
function isPalindrome(num: number): boolean {
    return num === +num.toString().split('').reverse().join('');
}
```

## Refactor Explaination

So the above code is nice, short, and sweet. The problem is that we didn't
really get a good chance to flex those big brains of ours! Fortunately LeetCode
to the rescue by asking us a follow up! Can we solve it without converting the
integer to a string? You betcha! The downside is that its gonna take a weeee bit
of work.

Lets consider this. We'll make a new variable, reversed, and we'll try and pop
the 'ones' digit value off of 123. So to remove that ones digit, we need to use
a modulo operation. 123 % 10 is 3, which is exactly what we need! So we'll add
that 3 to reversed. We do that with something like
`reversed = reversed * 10 + (the remainder)`. This shifts all the other digits
to the right to allow for the new incoming digit. Hopefully the table below with
clarify the end results further. Now to remove the ones digit from 123 itself we
need to do something like `num = Math.floor(num / 10)`. In this example, 123
becomes 12.3, but the floor of that is 12. We continue this until num becomes 0.

| Step | reversed | num |
| ---- | -------- | --- |
| 0    | 0        | 123 |
| 1    | 3        | 12  |
| 2    | 32       | 1   |
| 3    | 321      | 0   |

Now seeing that this just reversed the num, but that num is now 0, we know that
we need another variable to hold the initial value of num to compare. So we'll
take that into consideration as well. This seems like enough chit-chat, lets get
to slappin keyboards!

P.S. - One important note here! Negatives don't do so well in our reverser, but
fortunately, due to the - sign, negatives can never be palindromes! So uh... if
the num is less than zero, we always gotta return false.

## Refactor Solution

```
function isPalindrome(num: number): boolean {
    if(num < 0) return false;

    let original = num,
        reversed = 0;

    while(num){
        reversed = reversed * 10 + num % 10;
        num = Math.floor(num / 10);
    }

    return reversed === original;
}
```

## Closing

And there's some working code for checking if a number is a palindrome, just
without turning it into a string first! This is one of those kinds of follow up
questions that kind of changes a lot of things. It ends up making the problem a
completely different challenge, and turned this from a simple "do ya know how to
use methods" to a kind of "can you manipulate numbers at different places, aka
ones,tens,hundreds". Its ok if this one feels a little funky, and its also
totally ok if it feels a little mathy. The more you see this and the more you
practice with it your brain will make those connections repeatedly and before ya
know it these kinds of operations will be just another tool in the tool belt.
Next on our list of LeetCode problems we'll be taking down a super duper fun
one! The dreaded
<a href='/RomanToInteger.md'>**`LeetCode 13 - Roman to Integer`**</a>. See you
there!
