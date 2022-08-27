---
title: Bug report tool for OpenMandriva Lx
description: 
published: true
date: 2022-03-24T11:20:30.941Z
tags: documentation, user-guide, tools
editor: markdown
dateCreated: 2021-03-08T17:17:16.207Z
---

# Bug report tool for OpenMandriva Lx
The simple tool is called om-bug-report.

## The shortcuts
### Open OM Welcome and navigate to OM Features > *Bug report tool*

![om43-bugreportwelc.jpg](/images/om43-bugreportwelc.jpg)

### or open OpenMandriva Control Center and navigate to System > *Bug report tool*

![om43-bugreportomcc.jpg](/images/om43-bugreportomcc.jpg)

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

![om43-bugreportpsw.jpg](/images/om43-bugreportpsw.jpg)

![om43-bugreportpopup.jpg](/images/om43-bugreportpopup.jpg)

Then will create the omdv-bug-report file in your /home directory

![om43-bugreportfile.jpg](/images/om43-bugreportfile.jpg)

> **This file should be attached to any bugreport**.
{.is-info}

It will help speed up the work of bug squasher and simplify the work of the bug reporter by quickly providing detailed information.

\- 


