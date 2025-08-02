---
title: How to update system
description: How to update your Rock or Rolling system
published: true
date: 2025-08-02T19:12:19.690Z
tags: documentation, howto, user-guide
editor: markdown
dateCreated: 2021-02-19T15:43:53.051Z
---

# How to update system

> OpenMandriva policy on system upgrade is different.
> **Do not** use Discover for system upgrade.
{.is-danger}

<br>


Open Konsole and run the commands:
```
$ sudo dnf clean all ; dnf clean all ; dnf repolist
$ sudo dnf distro-sync --refresh --allowerasing
```

- or

![update-menu.png](/images/update-menu.png)


- or

![update-60-taskmanager02.jpg](/images/update-60-taskmanager02.jpg)

- or

![update-dnfdrake.png](/images/update-dnfdrake.png)
