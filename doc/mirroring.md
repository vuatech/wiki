---
title: Mirroring
description: 
published: true
date: 2020-12-21T23:52:09.347Z
tags: 
editor: undefined
dateCreated: 2020-03-14T19:10:14.516Z
---

# Mirroring
## List of mirrors

### Mirmon (Mirrors manager)
From here you can see if a mirror is regularly up to date
- https://mirmon.openmandriva.org/

### Mirrorbits
You can see where the mirrors are distributed around the world.
- http://mirror.openmandriva.org?mirrorstats

## Get the closest mirror
Mirrorbits can redirect automatically to the closest mirror from your location, here is an example with a simple txt file available on repositories:
- Immediate redirection: http://mirror.openmandriva.org/release_current/README.txt 
- Visual representation http://mirror.openmandriva.org/release_current/README.txt?mirrorlist

## T1 mirrors

our T1 mirrors are the mirrors directly updated from our build system (ABF).
They serve as origin for all other mirrors, and as fallback mirrors if Mirrorbits or ABF is down.

### T1 Mirrors list

We have three T1 mirrors
- **Yandex, Moscow, Russia**
-- URL http://mirror.yandex.ru/openmandriva/
-- `rsync://mirror.yandex.org/openmandriva/`
-- ftp://mirror.yandex.ru/openmandriva/
-- coord: 55.7522, 37.6156
- **The University of North Carolina, Chapel Hill, USA** 
-- URL: http://distro.ibiblio.org/openmandriva/
-- ftp://distro.ibiblio.org/openmandriva/
-- `rsync://distro.ibiblio.org/openmandriva/`
-- coord: 37.751, -97.822
- **The Federal University of Paraná, Brazil**
-- URL: http://openmandriva.c3sl.ufpr.br
-- `rsync://openmandriva.c3sl.ufpr.br/openmandriva/`
-- coord: 22.8305, -43.2192

## Setting up a mirror
If you want to support us by setting up a mirror for OpenMandriva Lx, please choose one of the three T1 servers as origin with, for instance, one of the following command samples:
- `rsync -av rsync://openmandriva.c3sl.ufpr.br/openmandriva/ /local/path`
- `rsync -av rsync://mirror.yandex.ru/openmandriva/ /local/path`
- `rsync -av distro.ibiblio.org::openmandriva/ /local/path/`
> Don't forget the ''TIME.txt'' file. It is needed by Mirmon and Mirrobits to work correctly.
>
> At least '''600GB''' of free disk space is needed
{.is-warning}


## T0 mirror

Our T0 mirror, ABF, is where packages are compiled and distributed. There are much  packages on it than on our other mirrors, such as source and debug packages, old release packages, personal repositories etc. 

Its content can be explored with this address:

- http://abf.openmandriva.org

Mirrorbits will always redirect to ABF if a file doesn't exist in any mirror. For instance: 
- http://mirror.openmandriva.org:8080/release_current/README.txt 
- http://mirror.openmandriva.org:8080/release_current/README.txt?mirrorlist