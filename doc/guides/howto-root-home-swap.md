---
title: How to have root, home, and swap partitions created during OM Lx installation
description: 
published: true
date: 2020-03-13T10:59:07.273Z
tags: 
---

# How to have root, home, and swap partitions created during OM Lx installation

OpenMandriva installer is [Calamares](http://calamares.io/).
It is easy, usable, beautiful, pragmatic, inclusive and distribution-agnostic.
Calamares includes an advanced partitioning feature, with support for both manual and automated partitioning operations.

> Note: When you read *Lx 4*, it is meant to include all 4.x versions like 4.0, 4.1, and 4.2. This how-to is applicable to all versions of OMLx including Cooker and Rolling as well as the Lx 4 family.
{.is-info}


To do pretty much anything you need with partitions you want to select <kbd>Manual partitioning</kbd>

![root-home-swap-01.png](/images/root-home-swap-01.png)

Notice that if you accept the default <kbd>Erase disk</kbd> it will create a `/boot/efi` and `/` partition only.
The installer by default no longer automatically creates a swap partition because on most all modern computers swap is not used anymore.

Select <kbd>Manual Partitioning</kbd>

![root-home-swap-02.png](/images/root-home-swap-02.png)

First we see how to set up an efi system with separate `/`, `/home` and `swap` partitions as well as the necessary `/boot/efi` for the efi booting. If you use MBR partition table you do not need to create a `/boot/efi` parition.
The `/boot/efi` partition should be labeled with `boot`. (The partitioner will automatically label it a `esp`.)

The first step is to select <kbd>New Partition Table</kbd>
If the system is efi or uefi boot it must be a `GPT` partition table.
If it is legacy boot you can select either `MBR` or `GPT`. If you don't know which to use select the more up to date `GPT`. Also if user has multiple hard drives or SSDs they all need to have the same partition table type or there can be problems. So all `GPT` or all `MBR`

![root-home-swap-03.png](/images/root-home-swap-03.png)

Next we will create `/boot/efi`, `/`, `/home`, and swap in that order.
The only critical factor in the order is that the `/boot/efi` needs to be first the others can be in any order.

`/boot/efi` is typically a 300 MB partition and needs to be fat16 or fat32 to work. In some other installers its file system type will be called vfat.

So we create them one at a time.
Select <kbd>Create</kbd>

![root-home-swap-04.png](/images/root-home-swap-04.png)

Follow the steps in the dialog box and you will end up with something like this

![root-home-swap-06.png](/images/root-home-swap-06.png)

If you have what you want select <kbd>Next</kbd> and when installed your new system will have the separate root, home, and swap partitions.

Note that `/boot/efi` is a the top of the list in first place. This is necessary.

> Note that your swap partition is probably never going to be used. Only a small minority of users these days really need a swap partition. Those that do need swap already know who you are and can adapt accordingly. Usually swap would be needed by really old computers with not enough RAM to run Lx 4 to begin with. How much RAM is enough? Ideally 4 GB. We do have users running Lx 4 with 2 GB. The Release Notes for Lx 4.0 and 4.1 do say 2 GB and the Calamares installer requires 2 GB. Upgrading the amount of memory in a computer, whether it’s a desktop, tower, or laptop, notebook, is both easy and not that expensive these days. So if your computer is short on memory do consider upgrading.
Swap also may still be used on computers doing very intense level of mathematical or scientific calculating or maybe really intense graphic applications. But those users will know what they need.
{.is-info}


This is a screenshot of what the <kbd>Create</kbd> dialog window should look like for your `/boot/efi` partition on `UEFI/EFI` system:

![root-home-swap-05.png](/images/root-home-swap-05.png)

\-
