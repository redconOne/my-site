---
title: 'Intersection of Two Arrays II'
date: 2023-02-06
draft: false
github_link: ''
author: 'Ming Lee Ng'
tags:
  - LeetCode 350
  - Array
  - Hash Table
  - Two Pointers
  - Binary Search
  - Sorting
image: /images/blog/blog3.jpg
description: 'The Everyday Persons Guide to LeetCode #350'
toc:
socials:
---

## Introduction

Hello and welcome! I'm Ming Lee, and today we're going to cover **How to solve LeetCode 350 - Intersection of Two Arrays II - in JS/TS :zap:**

Same as always we're gonna solve this, and we're gonna do it without the big fancy words because this is for regular folx! Keeping it nice and casual
round these parts! Movin' on...

## Problem

<b><a href='https://leetcode.com/problems/intersection-of-two-arrays-ii/'>`LeetCode 350 - Intersection of Two Arrays II`</a></b>

Given two integer arrays nums1 and nums2, return an array of their intersection. Each element in the result must appear as many times as it shows in
both ararys and you may return the result in any order.

## Explanation

Ok, so this is very similar to the last problem, with the exception that we need to ensure that we return all the intersecting elements, not just a
set. Now I'll start off by saying that my favorite way to solve this problem is probably by sorting and using a two-pointer method, but I don't think
that's necessarily the easiest way to go about this. One of the more simple ways, in my opinion, is to use hashmaps.

So lets start off by declaring a result array and two basic hashmap objects. Something like this

```
const result: number[] = [];
const map1: { [key: number]: number } = {};
const map2: { [key: number]: number } = {};
```

From here we need to populate these objects. Lets start by iterating over nums1. We need to ensure that every number in nums1 is accounted for so that
nums1[num] === numberOfOccurences. That should look a little something like this.

```
for(const num of nums1)
  if(map1[num]) map1[num]++;
  else map1[num] = 1;
```

We need to do the same thing for nums2 and map2. Once that is completed we need to compare these objects. We can handle that with yet another for loop
(I know there are a lot of for loops in here, but hang in there). Inside that for loop we need to compare the number of occurences per number in map1
to map2 and push that into result. This should look a little something like the following:

```
for(const key in map1){
  const total1 = map1[key];
  const total2 = map2[key] || 0;
  let min = Math.min(total1, total2);
  while(min){
    result.push(+key);
    min--;
  }
}
```

As you can see here, first we find the number of occurences and store those into the total variables for ease of use. We then find out the minimum. If
total2 doesn't have that particular number the minimum will be zero and we won't push anything. We then push the key into result (cast as an int) the
minimum number of times. Lastly we return result. Thats it! Lets see how it looks altogether.

## Solution

```
function intersect(nums1: number[], nums2: number[]): number[] {
  const result: number[] = [];
  const map1: { [key: number]: number } = {};
  const map2: { [key: number]: number } = {};

  for(const num of nums1)
    if(map1[num]) map1[num]++;
    else map1[num] = 1;

  for(const num of nums2)
    if(map2[num]) map2[num]++;
    else map2[num] = 1;

  for(const key in map1){
    const total1 = map1[key];
    const total2 = map2[key] || 0;
    let min = Math.min(total1, total2);
    while(min){
      result.push(+key);
      min--;
    }
  }

  return result;
}
```

## Closing

Whew! That was a wild one, but super fun! I know it might seem a little bit complicated, but I think this is the **simplest** way to solve this one.
Its not terrible either, as we're still hitting linear run-times, but it could definitely be improved on. Next we'll be working on
<a href='../validperfectsquare/'>**`LeetCode 367 - Valid Perfect Square`**</a>! See you then!
