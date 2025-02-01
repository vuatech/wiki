---
title: How to configure printer in OMLx
description: 
published: true
date: 2025-01-14T13:18:00.942Z
tags: documentation, howto, user-guide
editor: markdown
dateCreated: 2020-03-09T18:43:12.417Z
---

# How to configure printer in OMLx
Turn your printer on and see if it is automatically configured. Pay attention to whether the right driver was installed.

If printer was auto configured and you have correct driver you are all set.

If it was not, turn off your printer.

Open *Printer Settings* aka `system-config-printer` and remove your printer.
If the correct driver was not installed by default we will need to add a software package.

The next step is to determine what software to add for your printer.

In OpenMandriva Lx this is most likely to be a 'task-printing' package specific to your printer brand.
The packages are:
- task-printing-canon
- task-printing-epson
- task-printing-hp
- task-printing-lexmark
- task-printing-okidata
- brlaser (for Brother printers)
- task-printing-misc

Install the package that matches your brand or the misc package if none do.

Example using okidata:
```
$ sudo dnf install task-printing-okidata
```
Now turn printer on again and it should then automatically configure itself (sometimes you might need to reboot for auto config to work).

If not seek help [here](https://forum.openmandriva.org/c/support/17)
