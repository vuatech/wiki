---
title: OpenMandriva Repositories tl;dr
description: 
published: true
date: 2020-05-18T08:27:57.935Z
tags: documentation, user-guide
---

# Repositories tl;dr
## Media Sources
We have four basic media sources: `/main`, `/unsupported`, `/restricted` and `/non-free`.
#### How to manage repositories with om-repo-picker

Application menu > Software Repository Selector (om-repo-picker)

![repositories01.jpg](/images/repositories01.jpg)

Or you can select OpenMandriva repo-picker in OM Welcome

![repositories07.jpg](/images/repositories07.jpg)

### main
`/main` is the core packages maintained by the OpenMandriva Lx team.
This includes anything featured in the install images as well as many more applications considered important. `/main/release` repository should always be enabled.

![repositories02.jpg](/images/repositories02.jpg)

**Common users should never enable** `/testing` **repos in stable release**.

![repositories02x.jpg](/images/repositories02x.jpg)

### unsupported
`/unsupported` represents community maintained packages. They are not supported by the core OpenMandriva Lx team and depend on package maintainers to update it.
There may be many packages that will not install and others that install but do not work properly. Users are welcome to use whatever they find in this repository that is working.
#### How to enable unsupported repo in om-repo-picker

![repositories03.jpg](/images/repositories03.jpg)

### restricted
`/restricted` contains libraries that are not installed by default due to legal concerns, such as patent issues.
The usage of these packages vary by country. OpenMandriva Lx is not responsible for their usage. If you believe that their usage is disallowed in your country please disable the restricted repositories.
#### How to enable restricted repo in om-repo-picker

![repositories04.jpg](/images/repositories04.jpg)

### non-free
`/non-free` contains applications and drivers that are distributed but do not meet the definitions of Free Software.
While we can adjust the packaging of such applications, we do not have the source code and therefore can not fix problems caused by anything in this repository.
#### How to enable non-free repo in om-repo-picker

![repositories05.jpg](/images/repositories05.jpg)

> Please note: for a few applications, such as Steam, you will need to enable **both `non-free` and `main 32bit`**
{.is-info}


![repositories06.jpg](/images/repositories06.jpg)

## After the changes
When you are done with your changes, run the following command in console
`$ sudo dnf clean all ; dnf clean all ; dnf repolist`

## More in depth
For a detailed explanation read [OpenMandriva Release Plan and Repositories](/doc/release-plan-and-repositories)
