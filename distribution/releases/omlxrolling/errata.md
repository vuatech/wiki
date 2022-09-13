---
title: OpenMandriva Lx ROME Errata
description: 
published: true
date: 2022-09-13T20:49:11.167Z
tags: rolling, rome
editor: markdown
dateCreated: 2021-04-24T05:57:30.543Z
---

# OpenMandriva Lx ROME Errata - Known Issues

## This page is a Work_In_Progress, got it?

> As with any release, there are still issues and bugs that may not have been resolved. This page documents those that may cause inconvenience and where possible details how they may be worked around.
{.is-info}

<br>
**Please read also [OMLx ROME Release Notes](/distribution/releases/omlxrolling/notes)**.

## Known Issues and workarounds
<br />

### NVIDIA Graphics Cards

Information to come. See WIP.

<br />

### NVME SSDs

NVME SSDs are normally recognized by ROME Live ISO. If for some reason they are not we have couple of workarounds under 'Troubleshooting' in the ISO Grub2 Menu that may work. They are (PCIE ASPM=OFF) and (NVME APST=OFF). We hope this works for most peoples hardware.
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

<br />

### GEOIP

Installer automatic GEOIP setting may not set the timezone correctly.

<br />

### How to configure printer

Turn your printer on and see if it is automatically configured. Pay attention to whether the
right driver was installed. If printer was auto configured and you have correct driver then
great, you are all set.
If it was not, turn off your printer. Open System Settings>Hardware>Printers or from terminal (Konsole) run:

`kcmshell5 kcm_printer_manager`

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

`sudo dnf install task-printing-okidata`

Now turn printer on again and it should then automatically configure itself (sometimes you
might need to reboot for auto config to work). If it doesn't you can configure it with System Settings>Hardware>Printers or run from terminal (Konsole):

`kcmshell5 kcm_printer_manager`.

Alternative method to set up a printer in ROME are to use CUPS (localhost:631 as url in browser). *For some hardware this may work better.*

If not seek help [here](https://forum.openmandriva.org/c/en/support).

<br />

### Discover new software

If you want to explore also additional repositories packages you will need to enable them
by means of Software Repository Selector and to refresh cache. To refresh cache you can use `--refresh` option like this:

`sudo dnf --refresh install foo_package`

`sudo dnf --refresh dsync` (command to upgrade your ROME system)

Or you can use `dnf clean all` like:

`sudo dnf clean all ; sudo dnf install foo_package`

`sudo dnf clean all ; sudo dnf dsync` (another command to upgrade your ROME system)

<br />
