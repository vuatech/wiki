---
title: How to update system
description: How to update your Rock or Rolling system
published: true
date: 2025-04-22T21:44:35.176Z
tags: documentation, howto, user-guide
editor: markdown
dateCreated: 2021-02-19T15:43:53.051Z
---

# How to update system

> OpenMandriva policy on system upgrade is different.
> **Do not** use Discover for system upgrade. Never.
{.is-danger}

<br>

## How to update Rock
- To update your Rock system open Konsole and run the commands:
```
$ sudo dnf clean all ; dnf clean all ; dnf repolist
$ sudo dnf upgrade
```



<br>

## How to update ROME
- To update ROME, your rolling system, open Konsole and run the commands:
```
$ sudo dnf clean all ; dnf clean all ; dnf repolist
$ sudo dnf distro-sync --allowerasing
```

- or

![update-menu.png](/images/update-menu.png)


- or

![update-60-taskmanager02.jpg](/images/update-60-taskmanager02.jpg)

- or

![update-dnfdrake.png](/images/update-dnfdrake.png)
