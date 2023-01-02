---
title: 'Valid Palindrome'
date: 2022-12-29
draft: false
github_link: ''
author: 'Ming Lee Ng'
tags:
  - LeetCode 125
  - String
  - Two Pointers
image: /images/blog/blog1.jpg
description: 'The Everyday Persons Guide to LeetCode #125'
toc:
socials:
---

## Introduction

Hello and welcome! I'm Ming Lee, and today we're going to cover **How to solve LeetCode 125 - Valid Palindrome - in JS/TS :zap:**

Same as always we're gonna solve this, and we're gonna do it without the big fancy words because this is for regular folx! Keeping it nice and casual
round these parts! Movin' on...

## Problem

<b><a href='https://leetcode.com/problems/valid-palindrome'>`LeetCode 125 - Valid Palindrome`</a></b>

A phrase is a palindrome if, after converting all uppercase letters into lowercase letters and removing all non-alphanumeric characters, it reads the
same forward and backward. Alphanumeric characters include letters and numbers.

Given a string s, return true if it is a palindrome, or false otherwise.

## Explanation

What a great problem! There are so many different ways to solve this, so don't feel intimidated if I don't mention a way that you're thinking about
handling this one!

Personally, since I know that we're only wanting to deal with lowercase letters I like to set str = str.toLowerCase(). This just makes things a little
simpler for me.

After that I like to ensure that all the characters are alphanumeric. You can do this by checking char codes OR by using regex, or a handful of other
ways. I'll be using regex here, but don't let that scare you off!

To create our replace regex we'll first need to set a range of things for our regex to look for. We want it to look for anything that isn't a
lowercase letter. So our regex should look like this /[^a-z]/ The brackets[] are for looking for ranges of things, and the ^ is a not operator for
regex. So anything not a-z gets found. But that's not all. We also want to look for anything not 0-9. So lets toss that in there and get this
/[^a-z0-9]/. We also want this to look globally through the string, not just the first instance, so we'll add the g (for global) flag onto the regex
and get this /[^a-z0-9]/g. Thats it! That's our regex for alphanumeric stuff!

So we'll do str = str.replace(/[^a-z0-9]/g, '') and this will remove all the non-alphanumeric stuff for us. From there we just have to check to see if
what's left is a palindrome. We can do this any number of ways. A for loop and check it from front to back, or you can see if str ===
str.split('').reverse().join('')

Personally I'm feeling a little lazy so I'm gonna split reverse join it, but feel free to do this any other way you want! My code looks a little like
the following...

## Solution

```

function isPalindrome(str: string): boolean {
  str = str.toLowerCase().replace(/[^a-z0-9]/g, '');
  return str === str.split('').reverse().join('');
}
```

## Closing

Good work! After all the crazy problems we've done this one should be a little more straight forward to wrap your brain around. Don't be discouraged
if there are a few bugs to work out though, that's completely normal! We'll have another straight-forward problem tomorrow when we address solving
<a href='../singlenumber/'>**`LeetCode 136 - Single Number`**</a>! See you then!
