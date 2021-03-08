---
title: OpenMandriva Repositories tl;dr
description: 
published: true
date: 2021-03-08T17:42:52.444Z
tags: documentation, user-guide, tools
editor: markdown
dateCreated: 2020-03-03T17:34:57.632Z
---

# Repositories tl;dr
## Media Sources
We have four basic media sources: `/main`, `/unsupported`, `/restricted` and `/non-free`.
#### How to manage repositories with om-repo-picker

Application menu > Software Repository Selector (om-repo-picker)

![om4.2-repopicker-01.jpg](/images/om4.2-repopicker-01.jpg)

Or you can select OpenMandriva repo-picker in OM Welcome

![om4.2-repopicker-02h.jpg](/images/om4.2-repopicker-02h.jpg)

### main
`/main` is the core packages maintained by the OpenMandriva Lx team.
This includes anything featured in the install images as well as many more applications considered important. `/main/release` repository should always be enabled.

![om4.2-repositories01.jpg](/images/om4.2-repositories01.jpg)

**Common users should never enable** `/testing` **repos in stable release**.

![om4.2-repositories02.jpg](/images/om4.2-repositories02.jpg)

### unsupported
`/unsupported` represents community maintained packages. They are not supported by the core OpenMandriva Lx team and depend on package maintainers to update it.
There may be many useful and up-to-date packages, as well as many that will not install or others that install but do not work properly. Users are welcome to use whatever they find in this repository that is working.
#### How to enable unsupported repo in om-repo-picker

![om4.2-repositories03.jpg](/images/om4.2-repositories03.jpg)

### restricted
`/restricted` contains libraries that are not installed by default due to legal concerns, such as patent issues.
The usage of these packages vary by country. OpenMandriva Lx is not responsible for their usage. If you believe that their usage is disallowed in your country please disable the restricted repositories.
#### How to enable restricted repo in om-repo-picker

![om4.2-repositories04.jpg](/images/om4.2-repositories04.jpg)

### non-free
`/non-free` contains applications and drivers that are distributed but do not meet the definitions of Free Software.
While we can adjust the packaging of such applications, we do not have the source code and therefore can not fix problems caused by anything in this repository.
#### How to enable non-free repo in om-repo-picker

![om4.2-repositories05.jpg](/images/om4.2-repositories05.jpg)

> Please note: in OMLx 4.1, for a few applications, such as Steam, you will need to enable **both `non-free` and `main 32bit`**
This does not apply to 4.2 or newer releases.
{.is-info}


![repositories06.jpg](/images/repositories08.jpg)

## After the changes
When you are done with your changes, run the following command in console
`$ sudo dnf clean all ; dnf clean all ; dnf repolist`

## More in depth
For a detailed explanation read [OpenMandriva Release Plan and Repositories](/doc/release-plan-and-repositories)

\- 

