---
title: Mirroring
description: 
published: true
date: 2020-12-14T19:40:06.141Z
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
http://mirror.openmandriva.org:8080?mirrorlist

## Get the closest mirror
Mirrorbits can redirect automatically to the closest mirror, for instance
- Immediate redirection: http://mirror.openmandriva.org:8080/release_current/README.txt 
- Visual representation http://mirror.openmandriva.org:8080/release_current/README.txt?mirrorlist

## Setting up a mirror
Please follow this process:
* Use one of our T-1 mirrors,

`http://openmandriva.c3sl.ufpr.br` (Brazil)
`http://mirror.yandex.ru/openmandriva/` (Russia)
`http://distro.ibiblio.org/openmandriva/` (USA)

For example with command 
`rsync -av rsync://openmandriva.c3sl.ufpr.br/openmandriva/ /local/path`
`rsync -av rsync://mirror.yandex.ru/openmandriva/ /local/path`
`rsync -av distro.ibiblio.org::openmandriva/ /local/path/`
> Don't forget the ''TIME.txt'' file. It is needed by Mirmon and Mirrobits to work correctly.
>
> At least '''500GB''' of free disk space is needed
{.is-warning}


Note: the upstream is
`http://abf-downloads.openmandriva.org`

This server pushes only necessary directories and packages to Yandex and ibiblio.

Users should generally not use this server unless they need src.rpm packages, debug packages or packages from specific user contributed repo.

Mirrors should also avoid to sync from this server as there is much more data in it.

## Adding the urls to our lists
* Mirmon: send the url of your mirror to the workshop team (your mail will eventually be held for moderation, the first time).
We will add it to the lists.
* Media list: for each release (cooker, 4.0, rock (4.1), rolling, ...) the record is set as:

```
country=CountryName,city=CityName,latitude=[-]xx.y[y],longitude=[-]xx.y[y],bw=xxGB,version=VersionName,arch=ArchName,type=distrib,url=[ftp|http]://RootUrl/repository/ArchName
```

For example:
```
country=Brasil,city=Curitiba,latitude=-13.58,longitude=-51.85,bw=1GB,version=2013.0,arch=x86_64,type=distrib,url=ftp://openmandriva.c3sl.ufpr.br/openmandriva/openmandriva2013.0/repository/x86_64/
```

Please send also the relevant details for your mirror.

## Synchronize your mirror
* You may use **rsync** (`man rsync` for details)

```
/usr/bin/rsync -av --delete --delete-delay --numeric-ids --delay-updates --exclude=.~tmp~/ mirror.rosalinux.com::openmandriva/ /your_path
```

> You must use `--delete-delay` and `--delay-updates`, at the very least.
{.is-warning}

* The best is to synchronize every 6 or 12 hours

\-



