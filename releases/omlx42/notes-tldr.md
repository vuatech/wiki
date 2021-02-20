---
title: Notes tl;dr
description: OMLx 4.2 Notes tl;dr
published: true
date: 2021-02-20T22:04:50.042Z
tags: 4.2, releases
editor: markdown
dateCreated: 2020-07-15T10:08:13.956Z
---

# OMLx 4.2 Notes tl;dr

> **It is recommended that you read the extended version of** [OpenMandriva Lx 4.2 Release Notes](/releases/omlx42/notes) **as well as the** [OpenMandriva Lx 4.2 Errata](/releases/omlx42/errata) **at our wiki**
{.is-info}


## Available Media
This release is available as a live media DVD or USB flash drive (memory stick), downloadable in ISO format.
*Live media* means you are able to run OpenMandriva Lx straight from a DVD or memory stick and try it before installing it.

##  Recommended Hardware
OpenMandriva Lx requires at least 2048 MB of memory and at least 10 GB of hard drive space.

## Internet Connection
Calamares Installer checks if an Internet connection is available, but OpenMandriva Lx will install just fine even without. Simply install as you normally would and proceed to use your new system as normal.

## Virtual Machines
At this time the only virtualization software that OMLx ISOs are tested on is VirtualBox. The same hardware requirements apply when running in virtual machines.
For VirtualBox you must always have at least 2048 MB of memory or the system will fail to boot.

## Installer and EFI Support
This release of OpenMandriva Lx supports booting and installation with and without UEFI.
Note that secure boot is not supported.

## Recommended file system type for manual installation
Strongly recommended is ext4 file system type. For flash memory-based storage devices we make available F2FS.
Please note that Calamares cannot convert one partition type to another and preserve partition data.
If you run Calamares from the live image it is not possible to change an existing partition type. You will need to first delete the partition and recreate it as the type that you wish.

## Booting from USB
To transfer the live/installation image you may use *rosa-imagewriter* or via *dd*.
- rosa-imagewriter is available in our repos
 `sudo dnf --refresh install rosa-imagewriter`
 or you can get it [here](http://wiki.rosalab.ru/en/index.php/ROSA_ImageWriter)
 
- you may alternatively dd the image to your USB stick:
 `sudo dd if=<iso_name> of=<usb_drive> bs=4M`
 Replace `<iso_name>` with the path to the ISO and `<usb_drive>` with the device node of the USB drive, i.e. `/dev/sdb`.

*SUSE Studio ImageWriter also has been tested and works for burning ISO images to USB storage device.*

> Please do not use other usb-writing tools as some Windows tools (e.g. Rufus) truncate the volume name. This breaks the boot process.
{.is-danger}

## OpenMandriva repositories and software availability
**OMLx installed operating systems have just the /main repository enabled by default.**
For maximum availability of all software you will need to enable additional repositories called *unsupported*, *restricted*, and *non-free*.
Use the graphical utility [Software Repository Selector](https://wiki.openmandriva.org/en/doc/repositories-tldr) (om-repo-picker) to enable or disable the repo you wish to use.

While graphical tools (Discover, dnfdragora, etc.) are useful to find out available extra software, we strongly suggest to install packages from command line
 `sudo dnf --refresh install <package_name>`

 <br>
 
## Errata
-- **NVIDIA Graphics Cards**
This release includes the reverse engineered nouveau driver.
Users may use drivers from nvidia web site but they are not supported by OpenMandriva. Installing and maintaining any proprietary drivers is solely the users option and responsibility.

-- **NVME SSDs**
Some NVME SSDs may not be recognized by OMLx 4.2 Live ISO.
The Live ISO has 2 different workarounds. See more in [4.2/Errata#NVME SSDs](https://wiki.openmandriva.org/en/releases/omlx42/errata#nvme-ssds).

-- **GEOIP**
Installer automatically GEOIP setting may not set the timezone correctly.

-- **How to configure printer**
OMLx provides some 'task-printing' packages specific to your printer brand if the printer is not automatically configured.
Install the package that matches your brand or the misc package if none do.


<br>

## Helping the project
![om-donate.svg](/images/om-donate.svg){.align-left}If you want to help the project and support OpenMandriva, please consider [joining our team](https://www.openmandriva.org/en/article/get-involved) or making a [donation](https://www.openmandriva.org/donate) to keep the lights on!


 
