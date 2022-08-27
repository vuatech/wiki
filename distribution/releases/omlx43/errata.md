---
title: OpenMandriva Lx 4.3 Errata
description: 
published: true
date: 2022-05-29T19:37:11.619Z
tags: 4.3
editor: markdown
dateCreated: 2021-04-24T05:21:24.743Z
---

# OpenMandriva Lx 4.3 Errata - Known Issues

> As with any release, there are still issues and bugs that may not have been resolved. This page documents those that may cause inconvenience and where possible details how they may be worked around.
{.is-info}

As with any release, there are still issues and bugs that may not have been resolved.
This page documents those that may cause inconvenience and where possible details
how they may be worked around.

## Known Issues and workarounds
<br />

### NVIDIA Graphics Cards

This release includes the reverse engineered nouveau driver, which gives moderately good
support for most NVIDIA cards. For some dual-screen work it is actually better than
NVIDIA binary driver as it supports screen rotation on a second monitor useful for
monitors with rotatable screens.
Users may use drivers from nvidia web site but they are not supported by OpenMandriva.
These can not be supported by OpenMandriva for a number of reasons.
Installing and maintaining any proprietary nVidia drivers is solely the users option and
responsibility. 
There are community supported nvidia drivers available in non-free repository.
### NVME SSDs

There is a well known problem with some (especially newer) NVME SSDs and PCIE devices
where the SSD may not be recognized.
Problem is known and being worked on by OpenMandriva developers and upstream
developers.
Hardware recognition for nvme SSDs is considerably improved for OMLx 4.3.
This issue is of course very hardware specific.

On installed system user may wish to add this workaround to /etc/default/grub and
run update-grub2 to make workaround global. You would use the one that you found to
work on the Live ISO.
If (PCIE ASPM=OFF) worked for you then add:
`pcie=aspm=off`
to the lines:
`GRUB_DECLINE_LINUX_DEFAULT`
`GRUB_DECLINE_LINUX_RECOVERY`
in
`/etc/default/grub`
and then run:
`$ sudo update-grub2`

If (NVME APST=OFF) worked then add instead:
`nvme_core.default_ps_max_latency_us=0`

As always users are encouraged to ask questions about anything you do not understand
on our [forum](https://forum.openmandriva.org/).
### GEOIP

Installer automatic GEOIP setting may not set the timezone correctly.

### How to configure printer

Turn your printer on and see if it is automatically configured. Pay attention to whether the
right driver was installed. If printer was auto configured and you have correct driver then
great, you are all set.
If it was not, turn off your printer. Open System Settings>Hardware>Printers aka `kcmshell5 kcm_printer_manager`
and remove your printer.
If the correct driver was not installed by default we will need to add a software package.
The next step is to determine what software to add for your printer.
In OpenMandriva Lx this is most likely to be a 'task-printing' package specific to your
printer brand. The packages are:
•task-printing-canon
•task-printing-epson
•task-printing-hp
•task-printing-lexmark
•task-printing-okidata
•task-printing-misc
Install the package that matches your brand or the misc package if none do. Example
using okidata:
$ sudo dnf install task-printing-okidata
Now turn printer on again and it should then automatically configure itself (sometimes you
might need to reboot for auto config to work). If it doesn't you can configure it with System Settings>Hardware>Printers aka `kcmshell5 kcm_printer_manager`.
If not seek help [here](https://forum.openmandriva.org/c/en/support).

### Discover new software

If you want to explore also additional repositories packages you will need to enable them
by means of Software Repository Selector and to refresh cache.

### Multiboot

In the 'real world' multiboot works well most of the time but when there are problems
sometimes the solution is a workaround rather than a fix. These are just realities of
multiboot.
Also it is not currently possible for OpenMandriva QA to test our bootloader with every file
system type on every Linux distro, or even on "Top 10" Linux distros. The fact is that
whether multi-booting with Windows or other Linux distros we rely exclusively on users'
reports to know what does and what does not work regarding multi-booting.
One known problem encountered with OMLx bootloader is that OpenMandriva grub2 does
not create boot entries for openSUSE systems that use btrfs file system. OMLx grub2 does
work with openSUSE systems that use ext4 file system.
This is because openSUSE uses custom syntax for their btrfs patches for openSUSE os-
prober and grub2 packages that are not compatible with OMLx code. It is not presently
known if OMLx bootloader does/does not work with openSUSE with any other file system
types such as XFS or F2FS.
The workaround is for users to switch boot-loaders in UEFI firmware settings or BIOS.
Alternative may be to use openSUSE bootloader if it recognizes your OpenMandriva
system.
As users report multiboot issues we will fix what we are able to. Issues we are unable to fix
we will report in Errata for our OMLx Releases.

### Pipewire sound server

Some users may experience issues with the new Pipewire sound server. If so user may switch to the older pulseaudio sound server. To do this open Konsole and run the following copy and paste command:

`$ sudo dnf remove pipewire-pulse ; sudo dnf install pulseaudio-server`

### Updating Firefox

OpenMandriva's stable release aka Rock does not normally get updates to system and tool-chain packages. Because of this and because of how Mozilla develops Firefox sometimes Firefox packages will no longer build for our stable release. For users concerned about not having the latest version of Firefox a workaround is to install from [mozilla.org](https://www.mozilla.org/) the latest version of Firefox RR (Rapid Release) or [mozilla.org](https://support.mozilla.org/en-US/kb/switch-to-firefox-extended-support-release-esr) the latest version of Firefox ESR (Extended Support Release) version which gets all security updates but not feature updates.

### Zypper

The package zypper-needs-restarting may conflict with dnf-utils if installed.
As a workaround remove dnf-utils.

### Bluetooth

For bluetooth devices user may need to enable systemd bluetooth.service. Open Konsole
and run:

`$ sudo systemctl start bluetooth ; sudo systemctl enable bluetooth`

## What to do if I have a problem

Should you have problems please report in the [English Support forum](https://forum.openmandriva.org/c/en/support) with a descriptive title and enough of a description and information for someone to be able to help you. If your issue is a serious technical issue then please [file a bug report](https://github.com/OpenMandrivaAssociation/distribution/issues).

## Helping the project

The OpenMandriva development teams (Cooker & QA) are always looking for new
contributors to assist in creating and maintaining packages and to assist bugfixing and
testing. You are welcome to join us and help us in this work which is not only rewarding but
also tremendous fun!
If you feel that your talents do not lie in the realm of software, then the OpenMandriva
Workshop group, which is made up from the artwork, documentation, translation and
Communication teams, is always open for the submissions of artwork and translations.
New contributors who would like to help with these wide-ranging tasks should see the wiki
for more details, and to learn how to join! Alternatively you may use our [forum](https://forum.openmandriva.org).
It also costs time and money to keep our servers up and running. If you can, please [donate](https://www.openmandriva.org/en/Donate)
to keep the lights on!


## Please read also
[OMLx 4.3 Release Notes](https://wiki.openmandriva.org/en/distribution/releases/omlx43/notes).