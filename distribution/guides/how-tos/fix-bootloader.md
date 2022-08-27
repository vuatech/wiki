---
title: How to fix broken bootloader
description: 
published: true
date: 2022-04-02T16:07:14.522Z
tags: documentation, howto, user-guide
editor: markdown
dateCreated: 2020-09-10T21:59:11.289Z
---

# How to fix broken boot loader

OpenMandriva Lx uses grub2 bootloader, so we use grub2 commands.
The command to probe computer and write comprehensive grub2 menu is:
```
$ sudo grub2-mkconfig -o /boot/grub2/grub.cfg
```
In most circumstances this simpler command will work:
```
$ sudo update-grub2
```
Then to install the grub2 bootloader to the drive you wish to boot from:
```
$ sudo grub2-install /dev/xxx
```
Where you replace the “*xxx*” with the name of the drive you want to, or were booting OMLx from, like `sda` or if it is a nvme drive something like `nvme0n1`.

To do this obviously you need access to your OMLx system. It you do not have easy access you can try [Rescatux](https://sourceforge.net/p/rescatux/) or [Super Grub2 Disk](https://sourceforge.net/p/supergrub2/). For this task you may want to try Super Grub2 Disk first.

To find how your storage devices or drives are called, user can simply open KDE Partition Manager or from Konsole run the command:
```
$ sudo fdisk -l
```
<br>

### Additional information:
The commands `grub2-mkconfig` and `update-grub2` use the utility called ‘os-prober’ to probe the computer for other operating systems.
User can run this command independently to see if os-prober is correctly recognizing all other operating systems on users computer. Like this:
```
$ sudo os-prober
```

<br>

### Useful readings
[Grub2 manual](https://www.gnu.org/software/grub/manual/grub/html_node/index.html)
[How to Rescue a Non-booting GRUB 2 on Linux](https://www.linux.com/training-tutorials/how-rescue-non-booting-grub-2-linux/)
Some man pages: [1](https://aty.sdsu.edu/bibliog/latex/debian/grub2rescue.html) [2](https://www.gnu.org/software/grub/manual/grub/html_node/GRUB-only-offers-a-rescue-shell.html)



