---
title: Software Repository Selector
description: 
published: true
date: 2024-11-27T11:00:22.530Z
tags: documentation, user-guide, tools, howto
editor: markdown
dateCreated: 2020-03-03T17:34:57.632Z
---

# Software Repository Selector

## How to manage repositories with om-repo-picker

Application menu > Software Repository Selector (om-repo-picker)

![omrome.doc.repopicker-01.jpg](/images/omrome.doc.repopicker-01.jpg)


or select OpenMandriva repo-picker in OM Welcome

![omrome.doc.repopicker-02.jpg](/images/omrome.doc.repopicker-02.jpg)


## Media Sources
We have four basic media sources: `/main`, `/extra`, `/restricted` and `/non-free`

### main
`/main` is the core packages maintained by the OpenMandriva Lx team.
This includes anything featured in the install images as well as many more applications considered important. `/main/release` repository should always be enabled.

**Common users should never enable** `/testing` **repos in stable release**.

![omrome.doc.repopicker-03.jpg](/images/omrome.doc.repopicker-03.jpg)

If for some reason a common user will need to, do it at your own risk.

![omrome.doc.repopicker-04.jpg](/images/omrome.doc.repopicker-04.jpg)

### extra
`/extra` represents community maintained packages. They are not supported by the core OpenMandriva Lx team and depend on package maintainers to update it.
There may be many useful and up-to-date packages, as well as many that will not install or others that install but do not work properly. Users are welcome to use whatever they find in this repository that is working.
#### How to enable extra repo in om-repo-picker

![omrome.doc.repopicker-05.jpg](/images/omrome.doc.repopicker-05.jpg)

### restricted
`/restricted` contains libraries that are not installed by default due to legal concerns, such as patent issues.
The usage of these packages vary by country. OpenMandriva Lx is not responsible for their usage. If you believe that their usage is disallowed in your country please disable the restricted repositories.
#### How to enable restricted repo in om-repo-picker

![omrome.doc.repopicker-06.jpg](/images/omrome.doc.repopicker-06.jpg)

### non-free
`/non-free` contains applications and drivers that are distributed but do not meet the definitions of Free Software.
While we can adjust the packaging of such applications, we do not have the source code and therefore can not fix problems caused by anything in this repository.
#### How to enable non-free repo in om-repo-picker

![omrome.doc.repopicker-07.jpg](/images/omrome.doc.repopicker-07.jpg)

### Third party repositories
You may as well want to enable third party repositories

![omrome.doc.repopicker-08.jpg](/images/omrome.doc.repopicker-08.jpg)

## After the changes
When you are done with your changes, run the following command in console
`$ sudo dnf clean all ; dnf clean all ; dnf repolist`

## More in depth
For a detailed explanation read [OpenMandriva Release Plan and Repositories](/policies/release-plan-and-repositories)

\- 

