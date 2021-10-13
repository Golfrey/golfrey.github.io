---
title: x86 shr bug
toc: true
date: 2021-10-12 22:54:58
tags:
- csci 1650
categories:
- notes
description:
---

<!-- more -->
<!-- markdownlint-disable MD041 MD002--> 

## Bug description

When I am running something like `shr $edx, 0x20`, it doesn't set the `$edx` to 0. Why?

## Solve the bug

According to the document,  

"The destination operand can be a register or a memory location. The count operand can be an immediate value or register CL. The count is masked to 5 bits, which limits the count range to 0 to 31. A special opcode encoding is provided for a count of 1."

So, we can't use `0x20`.

## Thinking

Solving the bug takes me a lot of time. This sucks. Next time, read the document more carefully.