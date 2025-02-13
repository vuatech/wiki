---
title: OpenMandriva ROME Errata
description: ROME Errata
published: true
date: 2025-02-03T20:42:00.008Z
tags: rome
editor: markdown
dateCreated: 2023-02-28T15:18:26.632Z
---

# OpenMandriva ROME Errata - Known Issues

> As with any release, there are still issues and bugs that may not have been resolved. This page documents those that may cause inconvenience and where possible details how they may be worked around.
{.is-info}

**Please read also [ROME Notes](/distribution/releases/rome/notes)**.
<br>

## Known Issues and workarounds
<br>

### Steam
The game launcher/store steam is available in the `non-free` [*(1)*](https://wiki.openmandriva.org/en/policies/repositories-tldr#non-free) repositories of OpenMandriva - but it is known to crash when started for the first time, complaining about `steamwebhelper` not responding.

Since Steam is not Open Source, we cannot fix this - but we hope there will be a fixed version of Steam soon. In the mean time, there is a workaround: kill the hung `steamwebhelper` process (if you don't know how to do this, simply reboot) and just start steam again.

The second and all subsequent launches will work.
<br>

### NVIDIA Graphics Cards
Community members have made Nvidia proprietary drivers available. The `nvidia` driver contains the latest production driver.
Please read also [NVIDIA driver package version support](https://forum.openmandriva.org/t/5217)

<!--`nvidia-legacy` contains the latest legacy driver (currently 4xx version).-->
User can install the driver from OpenMandriva Welcome module.
Please keep in mind that the people that make these packages available are volunteering their time and knowledge. There might be a lag between a new kernel and the relevant nvidia packages builds. 
<!--
To install from Konsole (terminal):

`$ sudo dnf --refresh install nvidia --enablerepo=rolling-x86_64-non-free`
or
`$ sudo dnf --refresh install nvidia-legacy --enablerepo=rolling-x86_64-non-free`

If you installed ROME znver1 replace `x86_64` with `znver1`. 

-->
> These packages are kernel specific. At this time they will not install if a newer kernel version is installed on system than the kernel version this software is built for.
There is more about that [here](https://forum.openmandriva.org/t/about-nvidia-proprietary-driver-software/4770) and [here](https://forum.openmandriva.org/t/installing-nvidia-proprietary-drivers-in-rome/4742).
{.is-warning}

<br>

#### Known issues (all nvidia packages):
1. The code is closed source. We can not fix anything wrong with the code. Nvidia folks have to do that.

2. Plymouth boot splash may not work,

3. Virtual terminals may not work,

4. Kscreenlocker may not work,

5. If user uses `kernel-rc-desktop` they will need to install `nvidia-kmod-rc-desktop`. Or `kernel-rc-server` then `nvidia-kmod-rc-server`.

If user has an issue with the graphic performance of nvidia proprietary drivers OpenMandriva can not do anything about that. The people to contact are at the [nVidia developers linux forum](https://forums.developer.nvidia.com/c/gpu-graphics/linux/148). OpenMandriva can only deal with issues related to packaging of this 3rd party software and whether it does/does not install.
<br>

### How to install X11 on Plasma6 Wayland system
#### For Plasma6 user:

`sudo dnf in task-plasma6-x11 --refresh`

This gives user an option to compare X11 to Wayland. It is known that there are some problems with Wayland in Plasma6. This is a useful way to determine if the issue is in fact related to Wayland or not. Essential for support requests in OM Forum and Bug Reports. Also useful if for some reason Wayland does not work for user.

### How to install Wayland on Plasma6 X11 system
#### For Plasma6 user:

`sudo dnf in task-plasma6-wayland --refresh`

This gives users an option to compare Wayland to X11.


### NVME SSDs
NVME SSDs are normally recognized by ROME Live ISO. If for some reason they are not we have couple of workarounds under 'Troubleshooting' in the ISO Grub2 Menu that may work. They are (PCIE ASPM=OFF) and (NVME APST=OFF). We hope this works for most people's hardware.
This issue is of course very hardware specific.

Where it occurs, this problem is caused by buggy firmware in NVMe devices. If the maker of the device provides a firmware update, you may want to check if that fixes it without having to disable ASPM.

ASPM (Active State Power Management) can reduce the power consumption of NVMe devices - therefore disabling it is not recommended unless needed.

On installed system, user may wish to add this workaround to `/etc/default/grub` and run update-grub2 to make workaround global. You would use the one that you found to work on the Live ISO.

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

As always users are encouraged to ask questions about anything you do not understand on our [forum](https://forum.openmandriva.org/).
<br>

### Installing from Ventoy

One workaround is:

Copy your desired OMLx .iso file to the Ventoy partiton on the Ventoy flash drive. Boot that.

1. Open Konsole (terminal) and `cd /run/initramfs/omdv/LiveOS`
2. type `ls` and check that `squashfs.img` is present
3. Leave Konsole (terminal) open in that directory
4. Open OMLx Calamares installer and install your new system

It seems as long as that directory is open and `ls` shows `squashfs.img` is present then user will be able to install their desired OMLx system booted from the Ventoy flash drive.

If that does not work then perhaps this will:

1. Open Konsole (terminal) cd to “`/run/initramfs/omdv/LiveOS` ”,
then
`cp squashfs.img /live`
You have to do this step immediately after booting the 'Live' ISO or the folder `/run/initramfs/omdv/LiveOS` will either disappear or somehow not get recognized. After doing that `cp` then that folder will disappear so next:
2. `$ sudo mkdir /run/initramfs/omdv/LiveOS`
3. `$ sudo cp /live/squashfs.img /run/initramfs/omdv/LiveOS`
4. To check:
```
 $ ls -la /run/initramfs/omdv/LiveOS
total 2867796
drwxr-xr-x 2 root root         60 Oct 19 20:30 .
drwxr-xr-x 3 root root         60 Oct 19 20:29 ..
-r--r--r-- 1 root root 2936623104 Oct 19 20:30 squashfs.img
```
5. Install OMLx

<br>

### GEOIP
The installer's automatic GEOIP setting may not set your timezone correctly (it guesses your location based on your IP address).
If it detects your timezone incorrectly, simply select the correct timezone manually.
<br>

### Add/Remove favorites to Application Launcher
***In Plasma6*** this has been fixed.

***In Plasma5*** there still is an upstream bug with adding and removing favorites from Application Launcher
Users may choose from 2 workarounds:
•Add or remove  applications you wish to Favorites column in Application Launcher. Then right click on Application Launcher icon and select "Show Alternatives" and select to switch to one of the other launchers. Then right click on Application Launcher again and switch back.
•Add or remove  applications you wish to Favorites column in Application Launcher. Then logout and login.

### How to configure printer
Turn your printer on and see if it is automatically configured. Pay attention to whether the right driver was installed. If printer was auto configured and you have correct driver then great, you are all set.
If it was not, turn off your printer. Open System Settings>Hardware>Printers or from terminal (Konsole) run:

`kcmshell6 kcm_printer_manager`

(if you're using Plasma 5, use `kcmshell5` instead of `kcmshell6`) and remove your printer in the UI dialog.
If the correct driver was not installed by default we will need to add a software package.
The next step is to determine what software (if any) to add for your printer.
In OpenMandriva Lx this is most likely to be a 'task-printing' package specific to your printer brand. The packages are:

•task-printing-canon
•task-printing-epson
•task-printing-hp
•task-printing-lexmark
•task-printing-okidata
•task-printing-misc

Install the package that matches your brand or the misc package if none do. Example using okidata:

`sudo dnf install task-printing-okidata`

Now turn printer on again and it should then automatically configure itself (sometimes you might need to reboot for auto config to work). If it doesn't you can configure it with System Settings>Hardware>Printers or run from terminal (Konsole):

`kcmshell6 kcm_printer_manager`.

**Alternative method to set up a printer in ROME is to use CUPS (https://localhost:631/ as url in browser)**. *For some hardware this may work better.*

If not seek help [here](https://forum.openmandriva.org/c/en/support).

**Note:** If you have problems setting up a usb connected printer it may help to remove the packages `usbmuxd` and `ipp-usb`. Removing `ipp-usb` means you won’t be able to use "driverless" driver.
<br>

### Discover new software
If you want to explore also additional repositories packages you will need to enable them by means of [Software Repository Selector](/en/policies/repositories-tldr) and to refresh cache. To refresh cache you can use `--refresh` option like this:

`sudo dnf --refresh install foo_package`

Or you can use `dnf clean all` like:

`sudo dnf clean all ; sudo dnf install foo_package`

<br>

### Mesa and VirtualBox

VirtualBox running Plasma x11 ISO does not handle mesa 24.2.x very well ([upstream bugtracker report](https://gitlab.freedesktop.org/mesa/mesa/-/issues/11818)).
You may notice some glitches like missing shadows or other artifacts.
In real hardware or qemu (or any virtualization software that emulates a proper GPU) graphics is displayed correctly.
With the Plasma wayland ISO the issue does not appear.
Possible workaround for VirtualBox users:  downgrade to mesa 24.1.7.
<br>

### Graphics Controller in VirtualBox 7.0.x
The most recent OMLX install images may need VMSVGA controller to be set to boot successfully in VirtualBox 7.0.x.
<br>

### Sound in VirtualBox 7.0.x
Some users report issue with choppy or stuttering sound in OM VirtualBox 7.0.x package.
This issue seems to be related to users hardware. Developers are aware of this problem and actively looking for a solution. Users should keep in mind that sound in VirtualBox is an emulation and the process is subject to periodic issues. *Thus using VirtualBox for multimedia is likely to have periodic problems.*
<br>


### Multiboot
In the 'real world' multiboot works well most of the time but when there are problems sometimes the solution is a workaround rather than a fix. These are just realities of multiboot.
Also it is not currently possible for OpenMandriva QA to test our bootloader with every file system type on every Linux distro, or even on "Top 10" Linux distros. The fact is that whether multi-booting with Windows or other Linux distros we rely exclusively on user reports to know what does and what does not work regarding multi-booting.
One known problem encountered with OMLx bootloader is that OpenMandriva grub2 does not create boot entries for openSUSE systems that use btrfs file system. OMLx grub2 does work with openSUSE systems that use ext4 file system.
This is because openSUSE uses custom syntax for their btrfs patches for openSUSE os-prober and grub2 packages that are not compatible with OMLx code. It is not presently known if OMLx bootloader does/does not work with openSUSE with any other file system types such as XFS or F2FS.
The workaround is for users to switch boot-loaders in UEFI firmware settings or BIOS to the openSUSE bootloder.

As users report multiboot issues we will fix what we are able to. Issues we are unable to fix we will report in Errata for our OMLx Releases.
<br>

### Pipewire sound server
Some users may experience issues with the new Pipewire sound server. If so user may switch to the older pulseaudio sound server. To do this open Konsole and run the following copy and paste command:

`$ sudo dnf remove pipewire-pulse ; sudo dnf install pulseaudio-server`
<br>

### Zypper
The package `zypper-needs-restarting` conflicts with `dnf-utils` if installed.
As a workaround remove `dnf-utils`.
<br>

### Bluetooth
For bluetooth devices user may need to enable systemd bluetooth.service. Open Konsole
and run:

`$ sudo systemctl start bluetooth ; sudo systemctl enable bluetooth`
<br>

### SystemSettings
Some modules in SystemSettings may not display correctly at first launch.
They will do at next login.
<br>

## What to do if I have a problem
Should you have problems please report in the [English Support forum](https://forum.openmandriva.org/c/en/support) with a descriptive title and enough description and information for someone to be able to help you. Or for possible faster results contact us at [OpenMandriva Chat](https://wiki.openmandriva.org/en/team/chat) . If your issue is a serious technical issue then please [file a bug report](https://github.com/OpenMandrivaAssociation/distribution/issues).
<br>

## Helping the project
![om-donate-32px.png](/assets/om-donate-32px.png){.align-left}The OpenMandriva development teams (Cooker & QA) are always looking for new contributors to assist in creating and maintaining packages and to assist bugfixing and testing. You are welcome to join us and help us in this work which is not only rewarding but also tremendous fun!
If you feel that your talents do not lie in the realm of software, then the OpenMandriva Workshop group, which is made up from the artwork, documentation, translation and Communication teams, is always open for the submissions of artwork and translations.
New contributors who would like to help with these wide-ranging tasks should see the wiki for more details, and to learn how to join! Alternatively you may use our [forum](https://forum.openmandriva.org).
It also costs time and money to keep our servers up and running.
If you can, please [donate](https://www.openmandriva.org/Donate) to keep the lights on!
<br>

**Please read also**
[ROME Notes](https://wiki.openmandriva.org/en/distribution/releases/rome/notes)
<br>
![header-tr-rome.svg](/assets/header-tr-rome.svg){.align-abstopright}