---
title: OpenMandriva Lx 5.0 Errata
description: 
published: true
date: 2025-02-12T09:23:40.726Z
tags: 5.0
editor: markdown
dateCreated: 2022-12-26T17:59:33.144Z
---

# OpenMandriva Lx 5.0 Errata - Known Issues

> As with any release, there are still issues and bugs that may not have been resolved. This page documents those that may cause inconvenience and where possible details how they may be worked around.
{.is-info}

**Please read also [5.0/Release Notes](/distribution/releases/omlx50/notes)**.
<br />

## Known Issues and workarounds
<br />

### NVIDIA Graphics Cards
This release includes the reverse engineered nouveau driver, which gives moderately good support for most NVIDIA cards.
For some dual-screen work it is actually better than NVIDIA binary driver as it supports screen rotation on a second monitor useful for
monitors with rotatable screens.
Users may use drivers from nvidia web site but they are not supported by OpenMandriva for a variety of reasons.
Installing and maintaining any proprietary nVidia drivers is solely the users option and responsibility. 
There are community supported nvidia drivers available in non-free repository.
<br />

### NVME SSDs
There is a well known problem with some (especially newer) NVME SSDs and PCIE devices where the SSD may not be recognized.
Problem is known and being worked on by OpenMandriva developers and upstream developers.

![header-tr-50.svg](/assets/header-tr-50.svg){.align-abstopright}
