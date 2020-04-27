---
title: Using dnf in OpenMandriva Lx
description: 
published: true
date: 2020-04-27T12:06:14.071Z
tags: documentation, dnf, user-guide
---

# Using dnf in OpenMandriva Lx

> For full documentation and more commands see [DNF Command Reference](https://dnf.readthedocs.io/en/latest/command_ref.html)
{.is-success}


## Some basic commands

- install a package:
`$ sudo dnf --refresh install <package_name>`

- remove a package:
`$ sudo dnf remove <package_name>`

- search repositories for a package:
`$ sudo dnf search <package_name>`
Note: 'dnf search' will work with partial names as well

- cleanup any files and packages left in cache and to remove repository metadata:
`$ sudo dnf clean all ; dnf clean all`

- update your system:
`$ sudo dnf --refresh upgrade `

## Some other common dnf commands

`autoremove`
removes packages installed as dependencies that are no longer required by currently installed programs.
> Be careful and pay attention when using `dnf autoremove`. It is absolutely possible that this may remove something you don't want to remove. It is a good idea to keep a list of packages that were autoremoved so you know what to re-install if this happens.
Note: You can find autoremoved packages in `/var/log/dnf.log`
{.is-warning}


`check-update`
checks for updates, but does not download or install the packages

`downgrade`
reverts to the previous version of a package

`info`
provides basic information about the package including name, version, release, and description

`reinstall`
reinstalls the currently installed package

`repolist`
list enabled repositories

## Some common dnf options

`--allowerasing`
Allow erasing of installed packages to resolve dependencies. This option could be used as an alternative to the yum swap command where packages to remove are not explicitly defined. Use carefully, know what you are doing or you can break your system.

`-b, --best`
Try the best available package versions in transactions. Specifically during dnf upgrade, which by default skips over updates that can not be installed for dependency reasons, the switch forces DNF to only consider the latest packages. When running into packages with broken dependencies, DNF will fail giving a reason why the latest version can not be installed

`--disable, --set-disabled`
Disable specified repositories (automatically saves). The option has to be used together with the config-manager command (dnf-plugins-core)

`--disablerepo=<repoid>`
Disable specific repositories by an id or a glob. This option is mutually exclusive with `--repo`.

`--downloadonly`
Download the resolved package set without performing any rpm transaction (install/upgrade/erase).

`--enable, --set-enabled`
Enable specified repositories (automatically saves). The option has to be used together with the config-manager command (dnf-plugins-core)

`--enablerepo=<repoid>`
Enable additional repositories by an id or a glob

`--exclude=<package_name>`
Exclude certain packages from transaction

`--nobest`
Set best option to False, so that transactions are not limited to best candidates only

`-y, --assumeyes`
Automatically answer yes for all questions

## More
`$ dnf --help`
and
`$ man dnf`

The help menu takes about a minute to a minute and a half to read. The man page takes about 3-5 minutes.
Both are meant to be available for users to refer to as they use their system and need to find quickly how to do something.

There are also wiki pages and docs about dnf: [Using the DNF software package manager](https://docs.fedoraproject.org/en-US/quick-docs/dnf/), [Fedora wiki page](https://fedoraproject.org/wiki/DNF?rd=Dnf), and [DNF Command Reference](https://dnf.readthedocs.io/en/latest/command_ref.html).


