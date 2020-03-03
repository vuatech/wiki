---
title: OpenMandriva Repositories tl;dr
description: 
published: true
date: 2020-03-03T17:34:57.632Z
tags: documentation
---

# Repositories tl;dr
## Media Sources
We have these four basic media sources or categories:

### main
`/main` is the core packages maintained by the OpenMandriva Lx team.
This includes anything featured in the install images as well as many more applications considered important. `/main/release` repository should always be enabled.

### unsupported
`/unsupported` represents community maintained packages. They are not supported by the core OpenMandriva Lx team and depend on package maintainers to update it.
There may be many packages that will not install and others that install but do not work properly. Users are welcome to use whatever they find in this repository that is working.

### restricted
`/restricted` contains libraries that are not installed by default due to legal concerns, such as patent issues.
The usage of these packages vary by country. OpenMandriva Lx is not responsible for their usage. If you believe that their usage is disallowed in your country please disable the restricted repositories.

### non-free
`/non-free` contains applications and drivers that are distributed but do not meet the definitions of Free Software.
While we can adjust the packaging of such applications, we do not have the source code and therefore can not fix problems caused by anything in this repository. 

## More in depth
For a detailed explanation read [OpenMandriva Release Plan and Repositories](/doc/release_plan_and_repositories)
