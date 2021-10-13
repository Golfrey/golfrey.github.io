---
title: Golang 101
toc: true
date: 2021-10-09 16:43:39
tags:
- golang
categories:
- 101
description:
---

<!-- more -->
<!-- markdownlint-disable MD041 MD002--> 

## Basic Operation

### `if` operation

`else` and `else if` need to be the same line as the `}` of `if`. For example

```go
if root == nil && subRoot == nil {
        return true
    } else if root == nil || subRoot == nil {
        return false
    }
```

### `unordered_set` in golang

```go
m := make(map[int]struct{})
```



## String Operation

### Split string

For example, we want to split string s by " ", we can use code below:

```go
ss := string.Split(s, " ")
```

We can get a `[]string` , after the operations we want, we can use the `[]string` to reform string using code below:

```go
strings.Join(ss, " ")
```

### Get `[]byte` out of `string s` and use `[]byte` to reform `string`

```go
bytes := []byte(s)
string(bytes)
```

