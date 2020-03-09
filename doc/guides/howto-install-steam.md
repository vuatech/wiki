---
title: How to install Steam in OpenMandriva
description: 
published: true
date: 2020-03-09T21:04:41.194Z
tags: documentation, howto
---

# How to install Steam in OpenMandriva


## To install Steam in OpenMandriva Lx please perform the following steps:

### Start Software Repository Selector
- from Application menu

![install-steam-01.jpg](/images/install-steam-01.jpg)

- or from OM Welcome

![repositories07.jpg](/images/repositories07.jpg)

### Enable `/main 32bit` repository

![install-steam-02.jpg](/images/install-steam-02.jpg)

### as well as `/non-free` repository

![install-steam-03.jpg](/images/install-steam-03.jpg)

Click <kbd>OK</kbd> to apply

> You will be asked for root password
{.is-warning}


![install-steam-04.jpg](/images/install-steam-04.jpg)

### When you are done with your changes, run the following command in console
```
$ sudo dnf clean all ; dnf clean all ; dnf repolist
```

![install-steam-05.jpg](/images/install-steam-05.jpg)

### Install Steam

```
$ sudo dnf --refresh install steam
```

![install-steam-06.jpg](/images/install-steam-06.jpg)

![install-steam-07.jpg](/images/install-steam-07.jpg)

![install-steam-08.jpg](/images/install-steam-08.jpg)

### Application Menu > Games > Steam

![install-steam-09.jpg](/images/install-steam-09.jpg)

![install-steam-10.jpg](/images/install-steam-10.jpg)

![install-steam-11.jpg](/images/install-steam-11.jpg)

![install-steam-12.jpg](/images/install-steam-12.jpg)

![install-steam-13.jpg](/images/install-steam-13.jpg)

