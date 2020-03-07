---
title: QA/Getting Started
description: 
published: true
date: 2020-03-07T13:06:06.550Z
tags: documentation, qa
---

# Getting Started with QA
We are glad that you are interested in QA.
We have compiled this document to help you get started in helping us test OpenMandriva Lx.

You will need to use the command line to test more often than not. Make sure you have an accounts at [ABF](https://abf.openmandriva.org/), [OpenMandriva Issue Tracker](https://issues.openmandriva.org/), and [Github](https://github.com/OpenMandrivaAssociation).

QA Team daily communication takes place on Freenode IRC @ #openmandriva-cooker but remember that this is also where developers work so mind your IRC manners. Currently OpenMandriva contributor group is small enough that developers and QA work together on IRC. There is also a dedicated [QA Forum](https://forum.openmandriva.org/c/en/qa).

QA Team members are encouraged to actively attend weekly TC meetings or if unable to attend to read the [meeting logs](https://chwido.openmandriva.org/meetings/%23openmandriva-cooker/) to keep up with what is happening. They are announced [here](https://forum.openmandriva.org/t/2735).
TC meetings take place on Freenode IRC @ #openmandriva-cooker.

### Setting up your OpenMandriva Lx system
Because you'll probably be working with untested (with our OS at least) software, we strongly urge you to use a dedicated or virtual machine for testing. For QA work on hardware (recommended if at all possible) it is recommended to have Rolling installed on a separate partition so you have a 'stable' system on another partition in case something breaks during testing.

Pre-release software comes through the testing repositories. Packages in Main repository take precedence over those in other repositories. Packages in Unsupported and Non-Free repositories are responsibility of the package maintainer not OpenMandriva developers.

QA-Team members need a thorough understanding of [Release Plan and Repositories](doc/release-plan-and-repositories) and [Repository Policies](/dev/repository-policies). There will be more as we better document Openmandriva Lx but we like to keep documentation as simple and light as is feasible.

Workflow for packages is: Cooker > Rolling > Stable repo. Developers/package maintainers are responsible for initiating packages in Cooker and for moving them to Rolling/testing repos. Then QA takes over. Thus all QA Team members are encouraged to maintain a Rolling system where they can do package testing.

You can add the testing repositories with the OpenMandriva *Software Repository Selector* GUI or from command line

For Main repo only:

Rock system:
`sudo dnf config-manager --enable rock-testing-$ARCH`

Rolling system:
`sudo dnf config-manager --enable rolling-testing-$ARCH`

Replace `$ARCH` with your architecture.

For all testing repos:

Rock system:
`sudo dnf config-manager --enable rock-testing-$ARCH rock-testing-$ARCH-unsupported rock-testing-$ARCH-restricted rock-testing-$ARCH-non-free`

Rolling system:
`sudo dnf config-manager --enable rolling-testing-$ARCH rolling-testing-$ARCH-unsupported rolling-testing-$ARCH-restricted rolling-testing-$ARCH-non-free`

To disable simply replace `--enable` with `--disable`.

### Package Testing with Kahinah
Now that your system is set up, it's time to vote for the packages. Do they work? Are there really bad issues?

We use a system called [Kahinah](https://kahinah.rxu.tech/), which uses voting to determine which packages to push to the stable repository or not.

First, login to Kahinah. This uses your Github login.

You can see what packages are waiting to be tested in 'Recent Builds'. Give it a thumbs up or thumbs down, and let us know why.

The current procedure is that packages require 3 'Accept' votes to move forward, unless there are any 'Reject' votes. If there is even one 'Reject' vote it should be questioned and discussed before moving packages. Also packages that get stuck in Kahinah with no votes for over 7 days can be moved due to QA inaction. Discussion about this takes place on Freenode IRC channel #openmandriva-cooker.

### Testing new Alpha/Beta/RC ISOs
This is discussed [here](/dev/release-qa).

### Triaging New Bugs with Bugzilla
This process is in development at this time. (We need to implement something for triaging bug reports.) 