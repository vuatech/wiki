---
title: Macros
description: Information on macros
published: false
date: 2025-10-23T23:43:56Z
tags: cooker, development, guide, packaging
editor: markdown
dateCreated: 2025-10-23T23:43:56Z
---

# What are macros
In computer programming, a macro is a rule or pattern that specifies how a certain input should be mapped to a replacement output. You can think of these in the same way you would a keyboard shortcut or writing abbrivations.

## Location of macros files and general explaination
Open Mandriva stores macros in the /usr/lib/rpm/macros.d/ folder. You can view the file to more information about avaible macros and what the macros translate to. The output below is from the /usr/lib/rpm/macros.d/macros.systemd file.
```
#  -*- Mode: rpm-spec; indent-tabs-mode: nil -*- */
#  SPDX-License-Identifier: LGPL-2.1-or-later
#
#  This file is part of systemd.

# RPM macros for packages installing systemd unit files

%_systemd_util_dir /usr/lib/systemd
%_unitdir /usr/lib/systemd/system
%_userunitdir /usr/lib/systemd/user
%_presetdir /usr/lib/systemd/system-preset
%_userpresetdir /usr/lib/systemd/user-preset
```
In this macro file you can see the defined macro with % prefixing the name and the definition of the macro following. %_unit dir is equal to the path of /usr/lib/systemd/system. In spec files you will notice that some macros like %cmake_build do not require {} while in a file system related path requires them. This is a requirement for the RPM build system to distinguish regular text from macros in some instances. In spec files that packages a systemd service you will see %{_unitdir} despite the file above lacking the brackets.

## List of common macros.
### General RPM Spec macros
%{buildroot} = %{_buildrootdir}/%{name}-%{version}-%{release}.%{_arch}
%{_topdir} = %{getenv:HOME}/rpmbuild
%{_builddir} = %{_topdir}/BUILD
%{_rpmdir} = %{_topdir}/RPMS
%{_sourcedir} = %{_topdir}/SOURCES
%{_specdir} = %{_topdir}/SPECS
%{_srcrpmdir} =%{_topdir}/SRPMS
%{_buildrootdir} = %{_topdir}/BUILDROOT

### %build related macos

### %install related macros

### %file related macros
%{_sysconfdir} = /etc
%{_rundir} = /run
%{_prefix} = /usr
%{_bindir} = /usr/bin
%{_includedir} = %{_prefix}/include
%{_unitdir} = /usr/lib/systemd
%{_userunitdir} = /usr/lib/systemd/user
%{_libdir} = /usr/lib64 or /usr/lib for 32bit systems
%{py_sitedir} = %{_libdir}/python%{pyver}/site-packages/
%{_libexecdir} = /usr/libexec
%{_datadir} = /usr/share
%{_docdir} = %{_datadir}/doc
%{_iconsdir} = /usr/share/icons
%{_infodir} = %{_datadir}/info
%{_mandir} = %{_datarootdir}/man
%{_localstatedir} = /var
%{_sharedstatedir} = /var/lib
%{_datadir}/bash-completions/completions/
%{_datadir}/fish-completions/completions/
%{_datadir}/zsh-completions/completions/
