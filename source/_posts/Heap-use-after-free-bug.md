---
title: Heap use after free bug
toc: true
date: 2021-10-26 20:42:52
tags:
- leetcode
categories:
- notes
description:
---

<!-- more -->
<!-- markdownlint-disable MD041 MD002--> 

## "Heap use after free" error in LeetCode Online Judge

Why this would happen is because I doesn't terminate the LinkList well. I may cause a cycle to occur. 