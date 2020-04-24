---
title: OpenMandriva Lx 4.1 Errata
description: 
published: true
date: 2020-04-24T16:39:16.241Z
tags: 4.1
---

# OpenMandriva Lx 4.1 Errata - Known Issues

> As with any release, there are still issues and bugs that may not have been resolved. This page documents those that may cause inconvenience and where possible details how they may be worked around.
{.is-info}


**It is recommended that you read the latest** [Release Notes](/releases/omlx41/notes) **on our wiki**.

## NVIDIA Graphics Cards
This release includes the reverse engineered nouveau driver, which gives moderately good support for most NVIDIA cards. For some dual-screen work it is actually better than NVIDIA binary driver as it supports screen rotation on a second monitor useful for monitors with rotatable screens.
Users may use drivers from nvidia web site but they are not supported by OpenMandriva. These can not be supported by OpenMandriva for a number of reasons.
Installing and maintaining any proprietary nVidia drivers is solely the users option and responsibility.

## NVME SSDs
There is a well known problem with some (especially newer) NVME SSDs and PCIE devices where the SSD may not be recognized. For our *Live* ISO there is a workaround described in [Release Notes](/releases/omlx41/notes).
Problem is known and being worked on by OpenMandriva developers and upstream developers.
The OM Lx 4.1 release includes kernel 5.5.0 and hardware recognition for nvme SSDs should be considerably improved.
It is known that some Samsung nvme SSDs that were not previously recognized are now with this kernel version. This issue is of course very hardware specific.

On installed system user may wish to add that workaround to `/etc/default/grub` and run `update-grub2` to make workaround global. You would use the one that you found to work on the *Live* ISO.

If `(PCIE ASPM=OFF)` worked for you then add:
`pcie=aspm=off`
to the lines:
`GRUB_DECLINE_LINUX_DEFAULT`
`GRUB_DECLINE_LINUX_RECOVERY`
in 
`/etc/default/grub` 
and then run:
`$ sudo update-grub2`

If `(NVME APST=OFF)` worked then add instead:
`nvme_core.default_ps_max_latency_us=0`

As always users are encouraged to ask questions about anything you do not understand on our [forum](https://forum.openmandriva.org/).

## GEOIP
Installer automatically GEOIP setting may not set the timezone correctly.

## How to configure printer
Turn your printer on and see if it is automatically configured. Pay attention to whether the right driver was installed. If printer was auto configured and you have correct driver then great, you are all set.
If it was not, turn off your printer. Open *Printer Settings* aka `system-config-printer` and remove your printer.
If the correct driver was not installed by default we will need to add a software package.

The next step is to determine what software to add for your printer.

In OpenMandriva Lx this is most likely to be a 'task-printing' package specific to your printer brand. The packages are:
- task-printing-canon
- task-printing-epson
- task-printing-hp
- task-printing-lexmark
- task-printing-okidata
- task-printing-misc

Install the package that matches your brand or the misc package if none do. Example using okidata:
`$ sudo dnf install task-printing-okidata`
Now turn printer on again and it should then automatically configure itself (sometimes you might need to reboot for auto config to work).

If not seek help [here](https://forum.openmandriva.org/c/en/support)

## Discover
With regard to software in the repositories, Discover may not display all available packages.
This is due to its cache not being cleared and repositories list not being fetched at the first start.
Workaround is: run the commands
```
$ sudo rm -rf /var/cache/PackageKit/* /var/cache/app-info/*
$ sudo pkcon refresh force
```
If you want to explore also additional repositories packages you will need to enable them by mean of [Software Repository Selector](/en/doc/repositories-tldr) and refresh cache again.




