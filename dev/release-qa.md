---
title: OpenMandriva Release QA
description: 
published: true
date: 2020-03-07T12:51:37.873Z
tags: 
---

# OpenMandriva Release QA
> 
> **THE RELEASE PROCESS**
{.is-info}


## ISO Install
#### Installation
The distribution should boot from the DVD ISO
The distribution should boot from a basic memory stick created using
`dd if=”openmandriva iso” of=”dev/sd*” bs=4M`

The graphical and text installs should function as specified.

The install process must work in different languages i.e. no missing translations.
Alternative keyboard layouts must work.

#### Graphical Install
The graphical install should occur at the most suitable resolution and colour resolution available from the system a minimum resolution of 1024 x 768 should be supported.

#### Administration and Artwork
The name of the release should be the current one.
The licence agreement should display and be correct in it’s wording.  (sign off docs reqd)
The release notes should be current for the release in question and should be labelled as such. (sign off docs reqd)
All artwork must be that approved for the current release. (sign off docs reqd)

#### General Properties
No installation action requiring user intervention should appear off-screen for the resolution chosen (OK buttons; APPLY buttons, etc).
Where possible the user should be able to return to the previous step in the installation process. Where this is not possible the user should be warned that there is no reversion or possibility of revision from the next step (i.e. partition formatting).

#### Boot Manager
The boot manager must work for other OS installs
The boot manager must properly update should an alternative kernel be installed.

#### Hardware
The release must install on designated hardware platforms.

#### Network
Both wired and wireless configuration should be achievable with minimal user interaction

#### Repositories
If network is available the install process should successfully add them to the package manager

#### X-Server
Automatic set-up of the X-server should function where drivers are not functional for the installed card the X-server should default to the VESA driver to provide a fail-safe option.

#### Window Manager
The chosen window should install without error if this fails an alternative basic window manager should be offered. Automatic start-up of the window manager should be offered during the install.

#### Printing
The cups server should be installed during the install process.

#### Sound
The sound server should install automatically audible confirmation for the user should confirm this. If there is no sound card or if sound installation fails an appropriate message should be displayed.

#### User Setup
The installer should call for the provision of a root password.
The installer should force the creation of at least one user.


## Start Up
#### Initial Boot
The boot flash should display properly on the monitor there should be no displacement of the image.

The boot manager should show the proper options for boot as a minimum:

*Open-Mandriva Linux
Failsafe boot (boot to single user root terminal)
Rescue system
SuperGrub Iso?*

#### Graphical Login
The graphical login manager should display all users (excluding system users).
The chosen user should be the one that last logged in. In the case of a new installation it it should be the first entry when users are sorted alphabetically (a to z)
The keyboard cursor should start in the password text entry box.
If a shutdown/general purpose menu is included all functions must operate correctly.
The login manager must not allow access to the window manager without a password.
It should be possible to start a CLI interface login from the graphical login manager.
 
#### Window Manager
After login the chosen window manager should startup without error
Visible indication of USB plugged devices should be easily seen. (including wireless and wired network devices)
In the case of USB disk/cdrom/memory drives these should all mount cleanly for the following  filesystems ext2, ext3, ext4, fat32, ntfs3g and any encrypted file system drivers that may be included with the operating system.

#### Servers
As a minimum Samba, Cups, ssh, nfs and ftp servers must function correctly

#### Software Maintenance
The auto-update system must function correctly when internet access is available.

#### Configuration
The Open Mandriva drakconf system should be fully operational.

#### Graphical Core Applications
The following list of applications should start without error and have the minimum of bugs.

#### System
Plasma Desktop
KDE configuration apps
Sound server (network sound should be functional)
Akonadi server
File indexing
Konsole

#### Office
Libre Office
Okular

#### Internet
Falkon
Firefox
Chromium
Chromium-pepper-flash
Browser Plugins
PDF support
Java
Kmail
Mozilla Thunderbird
Konversation IRC Client

#### File Management
Dolphin
(built in network access must also function)
Krusader

#### File Editors
Kwrite
Kate

#### Development
Kdevelop
Eclipse

#### Graphics
Gwenview
Krita
DigiKam

#### Sound & Video
...

#### Tools
...

#### Utilities
...

#### CLI Core Applications

mc
vim
ed
vi
nano
emacs?
Bash
sh
binutils
man
less
netstat
bind
dhclient
M4
bison
grep
awk
sed
make
Autoconf
libtool
pkgconfig
scons
rpm
urpmi
perl
python


## Criteria for release approval
- All the programs listed above must be functional and able to open, process, close and save a file where appropriate. There must be no outstanding security issues.
- There must be no bugs that seriously compromise the functionality of the system as far as the user is concerned for the core packages listed above. Bugs in supplementary packages and contrib that do not adversely affect the running for the os may be tolerated. Bugs that will not be tolerated are excessive disk usage, high system resource consumption, memory leaks, window manager lockup and and any form of system freeze.
- It must be possible to install a different kernel from the OM repository without problems.  The kernel installation script must properly update the boot manager and show the availability of the new kernel in the boot up screen. The original kernel must be renamed in such a manner as to make it clear that this was the original default kernel. The symbolic links which point to the default kernel must be properly updated.
- It must be possible to use the dkms system to update the drivers available in the default distribution this should include the available proprietary graphics drivers;
- It must be possible to achieve network connectivity and where available be able to access the Internet. This should be possible for both wireless and wired connections;
- No commonly used server must fail to start;
- The system must be able to print from all applications that provide this service;
- The packaging system and repos must be operational including OpenMandriva auto update;
- ISOs submitted for release must be properly named and dated.


## Checklist
QA Team and testers are encouraged to produce a detailed checklist for ISO with list of detected bugs.<br />
It should contain typical use cases like:

1. Does iso burns on usb stick
1. Does the grub/boot screen appears
1. Does the options in grub/boot screen works
1. Does ISO boot to multi-user.target
1. Does ISO boot to graphical.target
1. Does autologin for live user works
1. Does default graphical desktop shows after autologin
1. Does default graphical desktop is useable (basics, like menu, file manager, web browser)
1. Does ISO boot in VirtualBox
1. Does ISO install in VirtualBox

