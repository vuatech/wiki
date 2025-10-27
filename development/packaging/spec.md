---
title: Information on Spec file
description: Explaning spec files
published: false
date: 2025-10-23T23:43:56Z
tags: cooker, development, guide, packaging
editor: markdown
dateCreated: 2025-10-23T23:43:56Z
---
# What are spec files
Spec files are files that contain information and instructions. This is comparable to a recipe. Spec files are comprised of metadata section and build instructions section. Below are information on each section.
### Metadata
```
Name: Name of package which should match the .spec file name

Version: The upstream release number of the sofware

Release: The number of time this version of software has been release/packaged

Summary: A brief summary of the package

License: The license of the software being packaged

URL: The URL for more information about the software. Usually the upstream website or repository where the software is hosted

Source0: Path or URL to the compressed archive of the source code. The source code should be unpatched and downloadable without the ABF storage (no local paths for archives if possible.) Multiple sources can be added by increasing the number such as Source1, Source2, and etc.

Patch: Name of the patch to apply to the source code if necessary. Multiple patches can be added in the same fashion as source can be.

BuildArch: This is usually absent except for cases where the package is not architecture depenent like python. In cases of python BuildArch: can be defined as noarch. If the BuildArch: is not defined it will use the architecture of the building machine.

BuildRequires: A list of packages required to build a program. Multiple BuildRequires: lines are used when needed.

Requires: A list of packages to be installed with the software. Multiple Requires: can be used when needed.

ExcludeArch: Used in the case a specific piece of software can not be used on certain architectures

Conflicts: Conflicts are the inverse to Requires: If there is a package matching Conflicts, the package cannot be installed.

Obsoletes: This directive alters the way updates work. When the package is installed the package defined with the Obsoletes: tag will be removed as if it is an upgrade. This is useful for name changes on spec files or if the software being package is meant to replace another.

Provides: This directive adds a way to refer to a package. The most common spec file to use Provides: are library spec files and those that have development componets.

%description: This contains a full description of the software. It can span multiple lines and can be broken into paragraphs. 
```
### Build Items
```
%prep: Command or series of commands to prepare the software to be build. This section usually involves extracting archives and patching files

%build: Command or series of commands for building the software.

%install: Command or series of commands for copying the built artifacts from the %builddir to the %buildroot

%check: Command or series of commands to test the software

%files: A list of files that will be installed on the end users machine. 
```
