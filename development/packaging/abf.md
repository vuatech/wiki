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
The ABF is, as the name describes, an autmoted build farm that handles the building, testing, and publishing of packages and ISO.

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
