---
title: How to compile your own software
description: 
published: false
date: 2024-01-24T01:07:05.893Z
tags: clang
editor: markdown
dateCreated: 2024-01-24T00:23:36.493Z
---

# Clang
A unique feature of OpenMandriva is the use of *clang* as our primary compiler. 

>  GCC is still available but has been fully dropped in favor of CLANG since OpenMandriva version 5.0
>  It's not possible anymore to use gcc to compile kernel modules for example! {.is-warning}

## Get Started

1. Before compiling your own software, please make sure it does not already exist in one of our repositories.
2. You can also request our team to add the package from the forum or directly on github

## Quick Start

You can install the basic development tools from the OM Welcome application :
![om5-welcome-devtools.png](/images/om5-welcome-devtools.png)

From the command line you can type:

```bash
sudo dnf install task-devel task-c-devel task-c++-devel
```

Example of a make command to compile a software locally on your machine:

## Compiler

By default softwares might use gcc as a base. You need to try with clang.
Below is an example of a custm make command

```bash
make CC=clang CXX=clang++ LD=ld.lld AR=llvm-ar NM=llvm-nm OBJCOPY=llvm-objcopy OBJSIZE=llvm-size STRIP=llvm-strip -C ...
```

## Packing

If you want to go further, you are welcome to join our task force to package softwares. 