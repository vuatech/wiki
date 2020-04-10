---
title: Repository Policies
description: 
published: true
date: 2020-03-07T12:50:36.384Z
tags: 
---

# Repository Policies

## Cooker
Cooker is an experimental branch that can break at times.

Most things are ok to do here, including updating to a beta version or even a git/svn/cvs/hg/whatever snapshot of an upstream package.

To make sure you do not "surprise" other developers by breaking everything for them, major changes need to be coordinated by either:
- bringing them up in a TC meeting
- sending a pull request on the repository and waiting for others to accept it
- sending an email to the cooker ML and waiting for others' positive reply

Changes that need coordination include, but are not limited to:
- switching out a major system component for something else (e.g. Xorg > wayland, Qt 5 > Qt 6, wpa_supplicant > iwd, systemd > any other init system, ...); any such change should be tested in a personal repository first.
- update that will require a load of rebuilds (e.g. updating libpng to a version with a new soname)
- dropping a package used by many things (e.g. dropping qt5 when qt6 is out and has been stabilized)
- changes that are likely to break other people's hardware

Cooker is usually open for all types of development, but can be frozen at some times to consolidate efforts on one branch.

## Rolling
Rolling needs to be usable for normal people at all times. Stuff that breaks things badly can not go into Rolling.

To make sure Rolling is always usable:
- Anything sent to Rolling must be built in cooker first. Exception: something where cooker has a newer version of the same thing already, e.g. it can make sense to push LLVM 8.0.1 to Rolling if Rolling is at 8.0 even when Cooker has already moved on to the 9.0 branch.
- Developers send packages to `rolling/testing` - not `rolling/release` - when they think stuff is ready for general consumption. Moving stuff from `rolling/testing` to `rolling/release` is done by QA, to make sure packages have been tested in the rolling environment.
- Rolling should usually not use beta releases/snapshots of upstream software. There are exceptions to this rule, e.g. where upstream is caught in a "release never" cycle, a beta/snapshot is the only one that works in our environment, e.g. "stable" release still uses Qt 4 or Python 2, or there is other good reasons).
Rolling goes into freezes shortly before new releases are made, so releases can be made as essentially a snapshot of rolling/release.

## Rock
This is the stable release tree. It gets only important updates, such as security fixes or fixes for system crashes.

People who want the latest version of something should use Rolling instead.
This means people who use Rock want something that never breaks, special attention must be paid when making any change whatsoever in Rock.
- Anything sent to Rock must be built in Rolling first. Exception: something where cooker has a newer version of the same thing already, e.g. it can make sense to push LLVM 8.0.1 to Rock if Rock is at 8.0 even when Rolling has already moved on to the 9.0 branch.
- Developers send packages to `rock/testing` - not `rock/release` - when they think stuff is ready for general consumption. Moving stuff from `rock/testing` to `rock/release` is done by QA, to make sure packages have been tested in the Rock environment.
- Rock should usually not use beta releases/snapshots of upstream software. Be even more careful about this than Rolling. There are exceptions to this rule, e.g. where upstream is caught in a "release never" cycle, a beta/snapshot is the only one that works in our environment, e.g. "stable" release still uses Qt 4 or Python 2, or there is other good reasons.
- Updates should usually not change the user interface. People using Rock want something they are familiar with and do not want surprises.
- **If in doubt, do not do it**. People who want the update for something that is not important should use Rolling

