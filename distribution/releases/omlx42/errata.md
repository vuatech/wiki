---
title: OpenMandriva Lx 4.2 Errata
description: OMLx 4.2 Errata
published: true
date: 2021-11-23T19:28:27.518Z
tags: 4.2
editor: markdown
dateCreated: 2020-02-26T23:58:47.215Z
---

# OpenMandriva Lx 4.2 Errata - Known Issues

> As with any release, there are still issues and bugs that may not have been resolved. This page documents those that may cause inconvenience and where possible details how they may be worked around.
{.is-info}

<br>

**Please read also [OMLx 4.2 Release Notes](/distribution/releases/omlx42/notes)**.


## NVIDIA Graphics Cards
This release includes the reverse engineered nouveau driver, which gives moderately good support for most NVIDIA cards. For some dual-screen work it is actually better than NVIDIA binary driver as it supports screen rotation on a second monitor useful for monitors with rotatable screens.
Users may use drivers from nvidia web site but they are not supported by OpenMandriva. These can not be supported by OpenMandriva for a number of reasons.
Installing and maintaining any proprietary nVidia drivers is solely the users option and responsibility.

## NVME SSDs
There is a well known problem with some (especially newer) NVME SSDs and PCIE devices where the SSD may not be recognized.
Problem is known and being worked on by OpenMandriva developers and upstream developers.
Hardware recognition for nvme SSDs should be considerably improved. 
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
If it was not, turn off your printer. Open *Printer Settings* aka SystemSettings>Hardware>Printers and remove your printer. You can also acess the *Printer Settings* from Konsole (terminal) with:

```
$ kcmshell5 kcm_printer_manager
```
 
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
```
$ sudo dnf install task-printing-okidata
```
Now turn printer on again and it should then automatically configure itself (sometimes you might need to reboot for auto config to work).

If not seek help [here](https://forum.openmandriva.org/c/en/support)

## Discover
If you want to explore also additional repositories packages you will need to enable them by mean of [Software Repository Selector](/policies/repositories-tldr) and to refresh cache.


## Firefox localization

For languages other than English in Firefox Web Browser you need to set the language you wish to use in Firefox settings under Language and Appearance.

## Multiboot
In the 'real world' multiboot works well most of the time but when there are problems sometimes the solution is a workaround rather than a fix. These are just realities of multiboot.

Also it is not currently possible for OpenMandriva QA to test our bootloader with every file system type on every Linux distro, or even on "Top 10" Linux distros. The fact is that whether multi-booting with Windows or other Linux distros we rely exclusively on users' reports to know what does and what does not work regarding multi-booting.  

One known problem encountered with OMLx bootloader is that OpenMandriva grub2 does not create boot entries for openSUSE systems that use btrfs file system. OMLx grub2 does work with openSUSE systems that use ext4 file system.
This is because openSUSE uses custom syntax for their btrfs patches for openSUSE os-prober and grub2 packages that are not compatible with OMLx code. It is not presently known if OMLx bootloader does/does not work with openSUSE with any other file system types such as XFS or F2FS.

The workaround is for users to switch boot-loaders in UEFI firmware settings or BIOS.
Alternative may be to use openSUSE bootloader if it recognizes your OpenMandriva system.
As users report multiboot issues we will fix what we are able to. Issues we are unable to fix we will report in Errata for our OMLx Releases.

## Zypper
The package zypper-needs-restarting will conflict with dnf-utils if installed.
As a workaround remove dnf-utils.

## Bluetooth
For bluetooth devices user may need to enable systemd bluetooth.service. Open Konsole and run:
```
sudo systemctl start bluetooth ; sudo systemctl enable bluetooth
```

<br>

\- 