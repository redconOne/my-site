---
title: 'Word Pattern'
date: 2023-01-28
draft: false
github_link: ''
author: 'Ming Lee Ng'
tags:
  - LeetCode 290
  - Hash Table
  - String
image: /images/blog/blog3.jpg
description: 'The Everyday Persons Guide to LeetCode #290'
toc:
socials:
---

## Introduction

Hello and welcome! I'm Ming Lee, and today we're going to cover **How to solve LeetCode 290 - Word Pattern - in JS/TS :zap:**

Same as always we're gonna solve this, and we're gonna do it without the big fancy words because this is for regular folx! Keeping it nice and casual
round these parts! Movin' on...

## Problem

<b><a href='https://leetcode.com/problems/word-pattern/'>`LeetCode 290 - Word Pattern`</a></b>

Given a pattern and a string s, find if s follows the same pattern.

Here follow means a full match, such taht there is a bijection between a letter in pattern and a non-empty word in s.

## Explanation

Ok, so this one is worded kind of funny, but if we look at the example where pattern is 'abba' and the string is 'dog cat cat dog' what we're trying
to do is compare the letters of pattern to the words of string. So when the 'a' in pattern comes up it needs to be mapped to 'dog'. If 'a' ever comes
up in patter and the string is not 'dog' we would return false. We can handle stuff like this in a handful of different ways, but lets take a look at
solving this with a map.

So the first thing we need to do is declare a map. We also need to split s into an array of words.

```
const map = new Map();
const str = s.split(' ');
```

We also know that if pattern.length and str.length are not equal this must be false because there aren't enough words or pattern pieces to compare
them both. So if they aren't equal return false.

```
if(pattern.length !== str.length) return false;
```

From here we need to iterate over pattern. If the map does not contain pattern[i] we need to set the key as pattern[i] and the value as str[i] in map.
Else we verify that that particular pattern element is equal to its string counterpart.

```
for(let i = 0; i < pattern.length; ++i)
  if(!map.has(pattern[i]))
    map.set(pattern[i], str[i]);
  else
    if(map.get(pattern[i]) !== str[i]) return false;
```

Now here we're kinda done. We've verified that the pattern matches up with the string. But we haven't really checked if the string matches up with the
patter. So we need to do the same process, just instead of map.set(pattern[i], str[i]) we will use map.set(str[i], pattern[i]). Lets try and look at
what the code looks like altogether.

## Solution

```
function wordPattern(pattern: string, s: string): boolean {
  const map1 = new Map();
  const map2 = new Map();

  const str = s.split(' ');

  if(pattern.length !== str.length) return false;

  for(let i = 0; i < pattern.length; ++i)
    if(!map1.has(pattern[i]))
      map1.set(pattern[i], str[i]);
    else
      if(map1.get(pattern[i]) !== str[i])
        return false;

  for(let i = 0; i < str.length; ++i)
    if(!map2.has(str[i]))
      map2.set(str[i], pattern[i]);
    else
      if(map2.get(str[i]) !== pattern[i])
        return false;

  return true;
}
```

## Closing

Awesome! So that was a funky one, but I think its pretty fun. Now we can do all kinds of cool stuff, like reduce this function into something a little
better. We're currently using two for loops in here. Can you think of a way to reduce this down to a single for loop? Keep up the good work and the
practice! Looking forward to tackling <a href='../NimGame/'>**`LeetCode 292 - Nim Game`**</a>! See you then!
