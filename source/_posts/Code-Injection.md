---
title: Code Injection
toc: true
date: 2021-10-08 15:20:40
tags:
- csci 1650
- class
categories:
- notes
description:
---

<!-- more -->
<!-- markdownlint-disable MD041 MD002--> 

## Details in the process

### nop operation

\x90

### Setting the return value to the start of the buffer

Since we can control the buffer, we can control the flow of the program.

### System operation

Since we will be attracking some machines on the internet, we don't know exactly the enviornment settings of the machine. For example, we can use something like `env` to check the enviroment of our own.

### Jump $esp

We need to write the asm code we want to execute, for example `jmp $esp`

```bash
vim scode.asm
as -32 scode.asm -0 scode
objdump -d scode
```

Like we can see `ff e4` is the assembly code of `jmp $esp`

If we want to find the assembly code in library like `libc`, we can use

```bash
objdump -d /lib/i386-linux-gnu/libc.so.6 | egrep jmp | egrep ecx
```

We will use `info proc mappings` to find the lowest address of `libc` and add this to the address we find in the code up.