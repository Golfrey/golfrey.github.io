---
title: Return to libc
toc: true
date: 2021-10-20 22:04:32
tags:
- csci 1650
categories:
- notes
description:
---

<!-- more -->
<!-- markdownlint-disable MD041 MD002--> 

## Return to libc chaining

Reading [return-to-libc (ret2libc) technique](http://phrack.org/issues/58/4.html#article) is enough.

## Things to remind myself

Don't insert string before the start address of stack. Insert the string after all the code you insert. For example, the system() fuction may  use the stack and damage the string you insert.