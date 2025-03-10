---
title: How to update channel
description: 
published: true
date: 2025-03-10T18:03:06.852Z
tags: documentation, howto, user-guide, advanced
editor: markdown
dateCreated: 2020-04-28T08:42:49.215Z
---

# How to update channel
## How to upgrade from Rock to ROME (rolling)

To users new to OpenMandriva Lx we suggest to start with Rock stable release to learn how the system works then, if you wish so, migrate to ROME, the rolling edition.

As a *ROME user* you should be able to use command line and know basics of [dnf](/en/distribution/guides/software-management/DNF) package manager.
Also the user needs to read and understand [OpenMandriva Release Plan and Repositories](/en/policies/release-plan-and-repositories).

To upgrade to ROME:

- Open Software Repository Selector (`om-repo-picker`) 
Application menu > Software Repository Selector

![omlx43.doc.repopicker-01.jpg](/images/omlx43.doc.repopicker-01.jpg)

or select OpenMandriva repo-picker in OM Welcome

![omlx43.doc.repopicker-02.jpg](/images/omlx43.doc.repopicker-02.jpg)


- Go to the very first section 'Update channel'.

![om4.2-repopicker-03.jpg](/images/om4.2-repopicker-03.jpg)

- Select 'Rolling' from drop-down menu

![om4.2-repopicker-04.jpg](/images/om4.2-repopicker-04.jpg)

confirm by click on OK and when prompted enter your root password. This will take a while and the program window may become momentarily invisible so be patient.

By this action you have now changed the repositories from Rock to Rolling so you want to perform a system upgrade (`distro-sync`).

- To upgrade your system open Konsole and run the commands:
```
$ sudo dnf clean all ; dnf clean all ; dnf repolist
$ sudo dnf --allowerasing distro-sync
```

\-
