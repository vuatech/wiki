---
title: Information on ABF
description: Describing how the abf works
published: false
date: 2025-10-23T23:43:56Z
tags: cooker, development, guide, packaging
editor: markdown
dateCreated: 2025-10-23T23:43:56Z
---

# Information on ABF(Automated Build Farm)
## What is the ABF
The ABF stands for autmoted build farm. The ABF handles the building, testing, and publishing of packages and ISO.

### How does the ABF work
The ABF uses a spec and a .abf.yml file to build a package in an semi(?)-airgapped (connection to the internet is not allowed) network.
The spec file contains the build/packaging related information while the .abf.yml file contains the hash of the source files. In cases where the size of a file is low like a patch file or supporting scripts it is ususally okay to have those in a git instance where the spec file and .abf.yml is stored.

### Common problems with the ABF
Common problems users will have with the ABF is build errors, test failed, and in some cases builders that never finish building. Unlike the first two issues, the third issue is not exclusively user caused in many cases. 

## Build Error
Build errors have two main errors.

### 	Irrecoverable error encountered when uploading files to file store.
This error occurs during the download of a file. This can be an issue with the builder or an issue with the source repo. If the repo does not contain a valid .abf.yml or a valid .spec file the builder will display this error. In some cases you can catch the build logs in the webgui proceeding past the initial download of the repo. Other times it can be related to the storage of the source archive for the project or a builder might be having a tiff. General rule of thumb is if a new build is ran on multiple architecture and one has an irrecoverable error, its most likely is not anything cause by the user.

### Bad exit status from /var/tmp/rpm-tmp.JIuH0j (%conf/%build/%install/%check)
These errors are always user cause/resolved. It can be due to missing dependencies, files, commands, and etc. In the case of these errors you can identify the cause of the issue by the % entry. %conf refers to the %conf section of a .spec file. On the ABF you will have the option to view a build log in the same style as the build logs that are generated when building a package on a local machine. The general rule for reading a build log is to skip to the end and look for an error such as
```
DEBUG: RPM build errors:
DEBUG:     Bad exit status from /var/tmp/rpm-tmp.FsNMaX (%build)
```
Above this line will have the last command ran. See below for an example.
```
DEBUG: Executing(%build): /bin/sh -e /var/tmp/rpm-tmp.FsNMaX
DEBUG: + umask 022
DEBUG: + cd /builddir/build/BUILD/walker-2.6.2-build
DEBUG: + cd walker-2.6.2
DEBUG: + cargo build --release --offline --frozen
DEBUG: /var/tmp/rpm-tmp.FsNMaX: line 33: cargo: command not found
DEBUG: error: Bad exit status from /var/tmp/rpm-tmp.FsNMaX (%build)
DEBUG: RPM build errors:
DEBUG:     Bad exit status from /var/tmp/rpm-tmp.FsNMaX (%build)
```
Above shows the build logs for walker. You can see the ABF executed the %build phase of the spec file. The %build phase had the command ```cargo build --release --offline --frozen```
Including the package that contains the cargo command will resolve the issue. For more information on how to include packages, please refer to example entry.

### Tests failed
This error happens when installing the package. The most common cause is a missing required package or the package is older or the same version as the package previously built. The test log will contain all the information required to troubleshoot this issue. For more information please refer to the example entry.

## Post Publish
Once a package is published to the ABF it should become available in a few minutes. If the package is a library that has a major change or has a package that is dependent on it's specific version it is necessary to increase the ```Release:``` tag by 1 and rebuilding the package. Dependent packages can be determined by using ```dnf repoquery --whatdepends %{packagename}```. Below is an example of lib64hyprutils.
```
[omv@omv-x86-64 ~]$ sudo dnf repoquery --whatdepends lib64hyprutils
Updating and loading repositories:
Repositories loaded.
hypridle-0:0.1.7-3.x86_64
hyprland-0:0.52.1-1.x86_64
hyprland-guiutils-0:0.1.0-2.x86_64
hyprland-qtutils-0:0.1.5-3.x86_64
hyprlang-0:0.6.5-1.x86_64
hyprlauncher-0:0.1.3-3.x86_64
hyprlock-0:0.9.2-4.x86_64
hyprpaper-0:0.7.6-6.x86_64
hyprpicker-0:0.4.5-4.x86_64
hyprpwcenter-0:0.1.1-2.x86_64
hyprqt6engine-0:0.1.0-2.x86_64
hyprsunset-0:0.3.3-2.x86_64
hyprsysteminfo-0:0.1.3-7.x86_64
lib64aquamarine-0:0.9.5-3.x86_64
lib64hyprgraphics-0:0.3.0-1.x86_64
lib64hyprtoolkit-0:0.3.0-1.x86_64
lib64hyprutils-devel-0:0.10.2-1.x86_64
lib64hyprwire-0:0.1.1-1.x86_64
xdg-desktop-portal-hyprland-0:1.3.11-1.x86_64
```
Looking at the script output logs from the abf we can see that these packages requires lib64hyprutils package. Another way to test if the dependent packages need to be rebuilt is to install all applications from the ```dnf repoquery --whatdepends %{packagename}``` and install the non-debug RPM file generated by the build process after. The DNF command will return the something similar to the following below.
```
Failed to resolve the transaction:
Problem 1: problem with installed package
  - installed package xdg-desktop-portal-hyprland-1.3.11-1.x86_64 requires libhyprutils.so.9()(64bit), but none of the providers can be installed
  - package xdg-desktop-portal-hyprland-1.3.11-1.x86_64 from cooker-x86_64 requires libhyprutils.so.9()(64bit), but none of the providers can be installed
  - conflicting requests
 Problem 2: problem with installed package
  - installed package lib64hyprwire-0.1.1-1.x86_64 requires libhyprutils.so.9()(64bit), but none of the providers can be installed
  - package lib64hyprwire-0.1.1-1.x86_64 from cooker-x86_64 requires libhyprutils.so.9()(64bit), but none of the providers can be installed
  - conflicting requests
You can try to add to command line:
  --skip-broken to skip uninstallable packages
```
You will see the output above from time to time in cooker. If this appears in rome or rolling while using ```sudo dnf dsync``` then please report the issue.
