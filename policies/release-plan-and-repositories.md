---
title: OpenMandriva Release Plan and Repositories
description: 
published: true
date: 2022-04-02T15:57:01.218Z
tags: documentation
editor: markdown
dateCreated: 2020-02-28T17:02:32.116Z
---

# OpenMandriva Release Plan and Repositories

Before making any change regarding release or update channels if you are even a tiny bit unsure stop, do not do it, and ask for advice on our forum or Chat with OpenMandriva Team

## Release
A release is a group of software packages put together to form an operating system.
Each release is distinguished by its "version", like *Mandriva 2009*, *Windows XP*, *OpenMandriva Lx 2014*, *OpenMandriva Lx 4.2*, ect.
Releases are also called *Update Channels*.
Release, Rock, Rolling and Cooker are all different release versions/update channels of OpenMandriva Lx. The emphasis is on the word different.
**They must not be combined**.

## Repositories
Repositories are servers which contain sets of packages, literally .rpm files.
On OpenMandriva operating system software is packaged in .rpm files which contain the programs and libraries you need. These files can be downloaded and also some are included in .iso files as a specific "release version" for user installation.
Each OpenMandriva release version has its own repositories.
They are not interchangeable, **do not mix them**.
Users generally accesses these files with package management tools like [DNF](/distribution/guides/software-management/DNF), or previously URPM.
There are GUI tools for this also like dnfdragora, Discover, and previously RpmDrake.

## Release Plan
The "Release Plan", also known as "Update Channels", is a hierarchy of software packages grouped together (release versions) in order to accomplish certain goals.
As an example Cooker release/update channel is designed specifically for developers to work on even it they break things.
Another example is Rock release/update channel which is designed for ordinary computer users to use for daily functions and is designed to not break (literally designed to be "stable").

With the Release of OpenMandriva Lx 4.0 OpenMandriva the distribution has implemented a new release plan in order to better organize the workflow for package maintenance and streamline and speed up the release process. This is closely coordinated with our repository structure.
On a given system use only one release. **Do not mix releases/update channels or package conflicts are likely if not guaranteed.**

Releases are also known as "Update Channels". Each version above has it's own repositories. The repository or .repo files are found in the directory `/etc/yum.repos.d`. By name the repository names are respectively openmandriva-cooker, openmandriva-rolling, openmandriva-rock, and openmandriva-release.
Repositories are further defined and named according to arch. Example below.

- **Cooker (Unstable)**

Cooker is the development branch. This is where developers do the actual work of developing packages and the distro itself. Because of the nature of this continual work process Cooker breaks at times. That is correct.
We aren't saying Cooker *might break* we say quite honestly Cooker *will break*. 
If you are not used to problem solving on computers at a very high level Cooker is not for you.

- **Rolling**

Rolling release is still in development and not officially announced.
At present entire Rolling release is in testing stage and not yet ready for production use.

Rolling is where developers take packages when they believe they are ready for use.
Rolling is, as its name implies, a rolling release and will have the most up to date packages practical.
It is designed to be a working, usable system. Rolling users need to be able to handle some problem solving on their own as with any "bleeding edge" release. Also Rolling users should be familiar with and able to use the command line or terminal (Konsole) at times.

-   **Rock (Stable)**

Rock repositories consist of a symbolic link to the latest stable version of OpenMandriva. Currently Rock is linked to OM Lx 4.2. However when OMLx 4.3 is released, Rock will automatically be switched to OM Lx 4.3.

-   **Release (Stable)**

Release repositories are the latest stable versions of OpenMandriva Lx currently OM Lx 4.1 and 4.2. Release repositories stay with the same release. If you install OM Lx 4.2 and used Release repository instead of Rock you will stay with 4.2 repository.
The Release/Stable version would be the most stable and suitable for users that like things to stay as they are and just work. Package upgrades will be limited mostly to bug fixes, and security updates.
Keep in mind that any version will eventually reach EOL (End Of Life) and there will be no more updates of any kind.

And remember the following: On a given system use only one release.
**Do not mix release/update channels or package conflicts are likely if not guaranteed.**

The packaging workflow now is:
`Cooker/Unstable > Rolling > Release/Stable`
*Remember Rock is a symlink to Latest Stable Release.*

## List of Repository files

Using OM Lx x86\_64 example
*znver1 users will see znver1 instead of x86_64*

Each Release above has its own repositories. They are not interchangeable, do not mix them.

These are the repository files for OpenMandriva Lx x86\_64.
The i686 files are there only for the occasional install of 32-bit applications like Wine, Steam, or gaming apps **in 4.1**.
It is recommended to enable them only for installing and upgrading those specific packages and otherwise to leave them disabled. Otherwise weird, baffling and unforeseen problems may occur.
Keep in mind that any developers still developing for 32-bit "only" are monumentally behind the times as far as technical progress in Linux.

Repository files listed alphabetically as they are on users system

- **Cooker (Unstable)**

`openmandriva-cooker-i686.repo`
`openmandriva-cooker-i686-source.repo`
`openmandriva-cooker-x86_64.repo`
`openmandriva-cooker-x86_64-source.repo`

- **Release (Stable)**

`openmandriva-release-i686.repo`
`openmandriva-release-i686-source.repo`
`openmandriva-release-x86_64.repo`
`openmandriva-release-x86_64-source.repo`

- **Rock (symlink to latest Stable)**

`openmandriva-rock-i686.repo`
`openmandriva-rock-i686-source.repo`
`openmandriva-rock-x86_64.repo`
`openmandriva-rock-x86_64-source.repo`

- **Rolling ("Bleeding Edge")**

`openmandriva-rolling-i686.repo`
`openmandriva-rolling-i686-source.repo`
`openmandriva-rolling-x86_64.repo`
`openmandriva-rolling-x86_64-source.repo`

*znver1 users will see znver1 instead of x86_64*

Users do not normally use source.repo files, if you don't have a reason to use these leave them alone.

## Normally used repository files

To make this simpler the vast majority of x86_64 users will normally use **one only** of these four.

Repository files listed with most stable first/least stable last:

`openmandriva-release-x86_64.repo`
`openmandriva-rock-x86_64.repo`
`openmandriva-rolling-x86_64.repo`
`openmandriva-cooker-x86_64.repo`

*znver1 users will see znver1 instead of x86_64*

## Media Sources

With in each repository file listed above we have these four basic "Media" sources or categories:

- **main**

`/main` is the core packages maintained by the OpenMandriva Lx team. This includes anything included in the install images as well as many more applications considered important. /main/release repository should always be enabled. If your system is using Release or Rock repo file then /main/release/updates should also always be enabled.

- **unsupported**

`/unsupported` represents ''community maintained'' packages. These are not supported by the core OpenMandriva Lx team, and depend on package maintainers to update it. There are many packages in unsupported that will not install and others that install but do not work properly. Users are welcome to use whatever they find in this repository that is working. 

- **restricted**

`/restricted` contains libraries that are not installed by default due to legal concerns such as patent issues.
The usage of these packages vary by country. OpenMandriva Lx is not responsible for their usage!
**If you believe that their usage is disallowed in your country, please disable the restricted repositories**.

- **non-free**

`/non-free` contains applications and drivers that are distributed, but do not meet the definitions of [Free Software](https://en.wikipedia.org/wiki/The_Free_Software_Definition). While we can adjust the packaging of such applications, ''we do not have the source code and therefore can not fix problems caused by anything in this repository''.

## Explanation of what to enable in repository categories

You may enable any of the following with the Software Repository Selector (om-repo-picker) in the Application Launcher under System.
There is a How-to [here](https://forum.openmandriva.org/t/2726).

As a practical matter for any of the Release categories chosen one should enable the Main repository always. For Release (Stable) and Rock one would enable (using x86_64 system as example)

`/x86_64/main/release/`
`/x86_64/main/updates/`

*znver1 users will see znver1 instead of x86_64*

Whether to use any or all of Unsupported, Restricted, or Non-Free is user decision but if one chooses to do so one would also enable the /release and /updates for each. 

`/x86_64/unsupported/release/`
`/x86_64/unsupported/updates/`
`/x86_64/restricted/release/`
`/x86_64/restricted/updates/`
`/x86_64/non-free/release/`
`/x86_64/non-free/updates/`

*znver1 users will see znver1 instead of x86_64*

Rolling and Cooker differ in that there is no update category for these so one would simply remove the /updates entries from the above list.

For a little more explanation for Release/Stable and Rock one would be enabling either 2, 4, 6, or a maximum of 8 media categories.
For Rolling or Cooker one would be enabling between 1 and a maximum of 4 media categories. This is in normal circumstances.





