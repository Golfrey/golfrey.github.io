---
title: Shellcode Development
toc: true
date: 2021-10-13 15:31:55
tags:
- cdci 1650
categories:
- notes
description:
---

<!-- more -->
<!-- markdownlint-disable MD041 MD002--> 

## Tricks

### How to shorter codes

#### `mov` instruction

```assembly
mov		$0x167, %eax
```

using `push, pop and inc` instead.

```assembly
push  $0x67
pop 	%eax
inc		%ah
```

#### Set `edx` to `0x0 or 0xffffffff`

```assembly
cdf		(cltd)
```

### Create string on stack

```assembly
"\x68"		/* push			*/ /* execve("/bin/sh", NULL, NULL) */
"\x2f\x2f\x73\x68" /* "//sh"		*/
"\x68"		/* push			*/
"\x2f\x62\x69\x6e" /* "/bin"		*/
"\x89\xe3"	/* mov    %esp, %ebx	*/
```

