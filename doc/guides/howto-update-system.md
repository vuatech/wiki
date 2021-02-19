---
title: How to update system
description: How to update your Rock or Rolling system
published: true
date: 2021-02-19T15:43:53.051Z
tags: documentation, howto, user-guide
editor: markdown
dateCreated: 2021-02-19T15:43:53.051Z
---

# How to update system
## How to update Rock
- To update your Rock system open Konsole and run the commands:
```
$ sudo dnf clean all ; dnf clean all ; dnf repolist
$ sudo dnf upgrade
```

## How to update Rolling
- To update your Rolling system open Konsole and run the commands:
```
$ sudo dnf clean all ; dnf clean all ; dnf repolist
$ sudo dnf --allowerasing distro-sync
```
