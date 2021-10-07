---
title: Bit Manipulation
toc: true
date: 2021-10-07 11:12:02
tags:
- algorithm
categories:
- leetcode
description:
---

<!-- more -->
<!-- markdownlint-disable MD041 MD002--> 

## Basics

- Set Union

  `A|B`

- Set intersection

  `A&B`

- Set subtraction

  `A & ~B`

- Set negation All_BITS

  `^ A` || `~A`

- Set bit 

  `A |= 1 << bit`

- Clear bit

  `A &= ~(1 << bit)`

- Test bit

  `(A & 1 << bit) != 0`

- Extract last bit

  `A & -A` or `A & ~(A - 1)` 

- Remove last bit

  `A & (A - 1)`

- Get all 1-bits

  `~0`

## Tricks

- Sum of two Integers

  ```
  int getSum(int a, int b) {
  	return b == 0 ? a : getSum(a^b, (a&b) << 1);
  }
  ```



## Contribution

Thanks to LHearen.

[A summary: how to use bit manipulation to solve problems easily and efficiently](https://leetcode.com/problems/sum-of-two-integers/discuss/84278/A-summary%3A-how-to-use-bit-manipulation-to-solve-problems-easily-and-efficiently)



