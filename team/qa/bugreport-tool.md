---
title: Bug report tool for OpenMandriva Lx
description: 
published: true
date: 2021-03-08T17:19:01.814Z
tags: documentation, user-guide, tools
editor: markdown
dateCreated: 2021-03-08T17:17:16.207Z
---

# Bug report tool for OpenMandriva Lx
The simple tool is called omv-bug-report.

## The shortcuts
### Open OM Welcome and navigate to OM Features > *Bug report tool*

![om-bugreportwelc.jpg](/images/om-bugreportwelc.jpg)

### Or open OpenMandriva Control Center and navigate to System > *Bug report tool*

![om-bugreportomcc.jpg](/images/om-bugreportomcc.jpg)

## Informations collected
The tool will gather useful informations from:

- various configuration files (in /etc/*)
- various /proc entries (which let know informations about kernel configuration)
- grub configuration (the boot program)
- lspcidrake output (for PCI devices listing)
- lsusb output (for USB devices listing)
- dmidecode output (to get informations about hardware from the BIOS)
- systemctl –failed (to report systems or services that failed to be started)
- journalctl -b (for showing log of current boot)
- rpm -qa (for listing installed packages)
- gcc version (for the version of the compiler)

![om-bugreportpopup.jpg](/images/om-bugreportpopup.jpg)

Then all will be packed into an archive and will create the file omv-bug-report.log.zst in your /home directory

![om-bugreportfile.jpg](/images/om-bugreportfile.jpg)

> **This file should be attached to any bugreport**.
{.is-info}

It will help speed up the work of bug squasher and simplify the work of the bug reporter by quickly providing detailed information.

## Read your file content
The file is compressed with zst. You can extract the file and read the content with the command `unzstd`
```
$ unzstd omv-bug-report.log.zst
```

\- 


