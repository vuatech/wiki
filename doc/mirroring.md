---
title: Mirroring
description: 
published: true
date: 2020-12-14T20:06:57.684Z
tags: documentation
editor: markdown
dateCreated: 2020-03-14T19:10:14.516Z
---

# Mirroring
## List of mirrors

### Mirmon (Mirrors manager)
From here you can see if a mirror is regularly up to date
https://mirmon.openmandriva.org/

### Mirrorbits
You can see where the mirrors are distributed around the world.
http://mirror.openmandriva.org:8080?mirrorstats

## Get the closest mirror
Mirrorbits can redirect automatically to the closest mirror, for instance
- Immediate redirection: http://mirror.openmandriva.org:8080/release_current/README.txt 
- Visual representation http://mirror.openmandriva.org:8080/release_current/README.txt?mirrorlist

## T1 mirrors

our T1 mirrors are the mirrors directly updated from our build system (ABF).
They serve as origin for all other mirrors, and as fallback mirrors if Mirrorbits or ABF is down.

### T1 Mirrors list

`http://openmandriva.c3sl.ufpr.br` (Brazil)
`http://mirror.yandex.ru/openmandriva/` (Russia)
`http://distro.ibiblio.org/openmandriva/` (USA)

### Setting up a mirror
If you want to support us by setting up a mirror for OpenMandriva Lx, please choose one of the three T1 servers as origin with, for instance, one of the following command samples:
For example with command 
`rsync -av rsync://openmandriva.c3sl.ufpr.br/openmandriva/ /local/path`
`rsync -av rsync://mirror.yandex.ru/openmandriva/ /local/path`
`rsync -av distro.ibiblio.org::openmandriva/ /local/path/`
> Don't forget the ''TIME.txt'' file. It is needed by Mirmon and Mirrobits to work correctly.
>
> At least '''600GB''' of free disk space is needed
{.is-warning}


## T0 mirror

Our T0 mirror, ABF, is where packages are compiled and distributed. There are much packages on it than on our other mirrors, such as source and debug packages, old release packages etc. 

Its content can be explored with this address:

http://abf.openmandriva.org

Mirrorbits will always redirect to ABF if a file doesn't exist in any mirror. For instance: 
- http://mirror.openmandriva.org:8080/release_current/README.txt 
- http://mirror.openmandriva.org:8080/release_current/README.txt?mirrorlist