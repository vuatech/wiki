---
title: How to get a list of all packages included in the ISO
description: 
published: true
date: 2020-03-13T07:56:02.306Z
tags: 
---

# How to get a list of all packages included in the ISO


In live mode, open console and type:

```
rpm -qa|sort > pkglist-sort.txt
```
which will create a plain text document in your user `/home` directory named `pkglist-sort.txt`

The packages list is sorted A-Z

![pkglist.jpg](/images/pkglist.jpg)

> The simple trick applies not only for ISO/Live mode but also for installed systems.
> You can run the command any time you need to.
{.is-info}


If you wish a list of all the packages sorted by date, type:

```
rpm -qa --last > pkglist-last.txt
```

\-
See also
[How to get a list of the latest updates](/doc/guides/howto-latest-updates)
