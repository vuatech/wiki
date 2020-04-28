---
title: How to update channel
description: 
published: true
date: 2020-04-28T08:52:21.886Z
tags: documentation, howto, user-guide, advanced
---

# How to update channel
## How to upgrade from Rock to Rolling

To users new to OpenMandriva Lx we suggest to start with Rock stable release to learn how the system works then, if you wish so, migrate to Rolling.

A 'Rolling' user should be able to use command line and know basics of [dnf](/en/doc/using-dnf) package manager.
Also the user needs to read and understand [OpenMandriva Release Plan and Repositories](/en/doc/release-plan-and-repositories).

To upgrade to Rolling:

- Open Software Repository Selector (`om-repo-picker`) 

Application menu > Software Repository Selector

![repositories01.jpg](/images/repositories01.jpg)

You can also select OpenMandriva repo-picker in OM Welcome

![repositories07.jpg](/images/repositories07.jpg)

- Go to the very first section 'Update channel'.

![repositories02.jpg](/images/repositories02.jpg)

- Select 'Rolling' from drop-down menu, confirm by click on OK and when prompted enter your root password. This will take a while so be patient.

By this action you have now changed the repositories from Rock to Rolling so you want to perform a system upgrade (`distro-sync`).

- To upgrade your system open Konsole and run the commands:
```
$ sudo dnf clean all ; dnf clean all
$ sudo dnf --allowerasing distro-sync
```

\-
