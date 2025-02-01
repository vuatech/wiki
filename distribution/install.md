---
title: Install OpenMandriva Lx
description: 
published: true
date: 2024-08-20T10:30:18.197Z
tags: 
editor: markdown
dateCreated: 2021-10-02T20:03:48.871Z
---

***If you have any questions prior to installing OpenMandriva Lx please ask us at [OpenMandriva Chat](https://wiki.openmandriva.org/en/team/chat) or on the [OpenMandriva Support Forum](https://forum.openmandriva.org/c/support/17).*** People may be in different time zone so please give us time to answer.

# 1\. Transfer the downloaded image to a USB flash drive

To transfer the live/installation image to an USB storage device you may use:
ROSA-imagewriter, KDE isoimagewriter, SUSE Studio ImageWriter, dd command line.
Please do not use other usb-writing tools as some Windows tools (e.g. Rufus) truncate the volume name and will break the boot process. 

# 2\. Boot from USB flash drive

Most computers automatically boot from a USB stick. Simply insert it and turn on your computer or restart it. You should see a menu, prompting you to choose the different entries.

If your computer does not automatically boot from USB, try holding down the F12 key at first boot or ESC. With most machines, this will allow you to select the USB device from a system-specific boot menu.

F12 and ESC are the most common key to bring up your system’s boot menu, but F2 and F10 are common alternatives. If you’re not sure, look for a brief message at your system’s startup - it will often tell you which key to press to bring up the boot menu.

Else try to find the correct key over the web, or do not hesitate to ask for help at our forum or chat room.

## Boot from DVD
Boot from DVD is deprecated.

# 3\. Start OpenMandriva Lx live mode

You will first be asked to start live mode. It will automatically start after 30 seconds. Live mode can be used for testing the distribution without touching the disk space, or for installing the distribution.

![1](https://forum.openmandriva.org/uploads/default/optimized/2X/8/8c9727b79d2d14b3bbd0855fd324602ed1b3ff8f_2_690x283.jpeg)

From that menu you can change the language and keyboard layout. This has no incidence on keyboard layout and language for actual installation, which will be asked later.  
 

![2](https://forum.openmandriva.org/uploads/default/optimized/2X/5/542eb029a442b16f20ddabc2b689789badd39332_2_690x322.jpeg)

Please note that the default keyboard layout of live mode is US QWERTY, so it may be tricky if you want to set a user password for installation without actually checking the characters. The number of languages and layouts for live mode is very limited for live mode, but there are much more choice during actual installation later.

![3](https://forum.openmandriva.org/uploads/default/optimized/2X/d/dc104372eed37891b803654bbe9af53fcc7dc844_2_690x322.png)

# 4\. Welcome in OpenMandriva Lx live mode

![image](https://forum.openmandriva.org/uploads/default/optimized/2X/f/f834e3ba9e2380e64bdfdaa6cdb2a0f85a22905e_2_667x500.jpeg)

you can safely close or reduce the welcome window to display the desktop icons.

When you feel ready for the installation, click on the “install OpenMandriva Lx” icon.

![image](https://forum.openmandriva.org/uploads/default/original/2X/1/152f47602da6aaec3baade2c95341ae57837247d.png)

# 5\. Preparing the installation

First choose your language and click next.

![6](https://forum.openmandriva.org/uploads/default/optimized/2X/3/3ec3e0ddc0ad5c6b95d95814d54f7bd6268555ce_2_690x369.png)

Then choose your timezone according to this [list](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones#List) either by clicking on the map or using the menu. Then check the language and numbers and dates are correctly set and click next.

![7](https://forum.openmandriva.org/uploads/default/optimized/2X/b/b012db7a20f89cf37474ab6b36e4476b50e1aa01_2_690x369.jpeg)

You will first be asked to select your keyboard layout. If the installer does not guess the default layout correctly, you can modify it and check with the ‘Test Keyboard Layout’ field.

![8](https://forum.openmandriva.org/uploads/default/optimized/2X/6/6ffe4b3c63507fb964e06fb3679893997180bf63_2_690x369.png)

Here comes the most important moment of the installation, as it’s about how it will be installed on your hard drive. Depending on if you already have once or more operating system already installed on your disk, Calamares can offer you:

Some automated options :

-   Shrink an existing partition and install OpenMandriva Lx alongside any other OS already available on your system. If you have a Windows partition, this is the option you may want to choose to keep this operating system. (recommended for beginners)
-   Use an existing partition and it will replace all files and/or OS on that partition with a new install of OpenMandriva Lx. (advanced users)
-   Use the entire disk and will create one partition where all will be installed under root (administrator or super user), all other partitions will be removed. (beginners)

And manual option:

-   This method gives you the freedom to set any option, any filesystem and partition table, but leaves it entirely up to you to completely break the install too. Make sure you know what you are doing. Another page will be created for advanced partitioning. (expert users)

Alongside with the selected option, there is an option for swap file (there will be a dedicated thread for swap). Unless you know what you do, Swap to file is a good option.  
 

![image](https://forum.openmandriva.org/uploads/default/optimized/2X/4/438b7613cbcc876b9baa212e0300071490d70ce7_2_690x143.png)

Check the “encrypt system” option if you want to add a layer of security to your data. The system will ask you the password entered each time you start the system.

![image](https://forum.openmandriva.org/uploads/default/optimized/2X/d/d0cf1db41fef4319988fa69e1e11154479761477_2_690x163.png)

Create a user account, give a name to your computer and either give an administrator password (also called root password) or check “use the same password for the administrator account”

![image](https://forum.openmandriva.org/uploads/default/optimized/2X/e/e46e539f893a10323d4c7bef786ac4d49807fd9f_2_690x349.png)

After checking the summary of the installation, you can click install

![image](https://forum.openmandriva.org/uploads/default/optimized/2X/9/92932b3faacc4819d5120defad361a7722d3be59_2_690x455.png)

Wait for the installation process to finish.

![image](https://forum.openmandriva.org/uploads/default/optimized/2X/d/dd3cb650845245a372d776b1eade5b8763fc7158_2_690x455.jpeg)

Once done, click Done and restart your computer (you also can check “Restart now”).

![image](https://forum.openmandriva.org/uploads/default/optimized/2X/8/8d89ea930a3998a90533d7cedb6b354d8840725d_2_690x455.png)

Once your computer restart you can enjoy using OpenMandriva Lx.

# Notes

[Original source (forum)](https://forum.openmandriva.org/t/h/4223)

Read also:
* [How to create root, home and swap partition during installation](/en/distribution/guides/how-tos/howto-root-home-swap)
* [How to get a list of all packages included in isos](/en/distribution/guides/how-tos/list-packages-iso)
