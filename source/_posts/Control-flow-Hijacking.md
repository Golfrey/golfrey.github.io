---
title: Control-flow Hijacking
toc: true
date: 2021-10-07 20:05:36
tags:
- csci 1650
- class
categories:
- notes
description:
---

<!-- more -->
<!-- markdownlint-disable MD041 MD002--> 

## Make

We can use like `make file_dbg` to gdb something.

We can use like `make file_run` to run something.

If we look into this, we can see something like `-m32 -no-pie -fno-pic` . This is settings to make sure we see eveything same, to make sure the experiment go right.

## Socket connect

We can use command `nc` . If we want to connect port 7777 in lab machine faclab03, we can use `nc faclab03 7777` 

## Disassemble code outside GDB

```bash
objdump -d file
```

## Disassemble code inside GDB

If we want to disassemble fuction like main in GDB, we can use code below:

```bash
disassemble main
```

We can use single `disassemble` to see the current fuction's code.

## Setup a breakpoint in GDB

We can find out the address of the fuction we want to look. For example, 0x08044959d, we can use code below:

```bash
b *0x08044959d
```

`si` is step into; `ni` is next instruction. So we use `ni` if we want to escape inside of the fuction.

## Show proc mappings in GDB

```
info proc mappings
```

## Assembly Language Usage

### Call

call does two things, it stores next command address into stack, and push the address into eip.

### X command

x command examines the data located in memory at address.

```bash
[x]/<number><format><unit_size> <address>
```

- **number** optionally indicates that several contiguous elements, beginning at **address**, should be examined. This is very useful for examining the contents of an array. By default, this argument is 1. 
- **format** indicates how data should be printed. In most cases, this is the same character that you would use in a call to **printf()**. One exception is the format i, which prints an instruction rather than a decimal integer. 
- **unit_size** indicates the size of the data to examine. It can be **[b]ytes**, **[h]alfwords** (2 bytes), **[w]ords**, or **[g]iant** words. By default, this is bytes, which is perfect for examining instructions. 

For example, we can use `x/a $esp` to check the address of `$esp`

We can see `0x80495a2`

Since the machine we use is small endian, we can use `x/4xb $esp` to see `0xa2  0x95  0x04 0x08`

### Something Constant

api never change. We can use `man` command to see the input number of the command.

## Details in the process

### Think about `%ebp & %esp`

So we may encounter these two command.

```
push %ebp
mov %esp,%ebp
sub $0x218,%esp
```

So you backup `%ebp`first, then we use `%esp`to give `%ebp` as base pointer. Then we can allocate stack by changing the value of `%esp`.

### Function Parameters

We can find the first parameter on the top of the stack.

For example, if we do like `read(cfd, buf, BUF_LEN)`, then we use `x/3a $esp` then we will see like

```
0x4 oxbffffbbc 0x400
```

each one point to cfd, buf and BUF_LEN.

### Function Returns

When some call return, it will always store the return value into `$eax` 

### Nop Instruction

`nop` instruction doesn't do anything. It is for align purpose.

### Leave Instruction

It does two things. First, it copy `$ebp` to `$esp`. Second, it set `$ebp`to its back value.

### What the ebp says

Minus `$ebp` always tellsl us what is in the stack. Add `$ebp` tells us the fuction parameter and the return address of the fuction.

