---
title: How to install Steam in OpenMandriva
description: 
published: true
date: 2023-04-09T18:38:38.714Z
tags: documentation, howto, user-guide
editor: markdown
dateCreated: 2020-03-09T20:59:51.458Z
---

# How to install Steam in OpenMandriva


## To install Steam in OpenMandriva Lx please perform the following steps:

### OM Welcome > Applications > Games

Click on  Steam


![omlx43.doc.steam-01.jpg](/images/omlx43.doc.steam-01.jpg)

![omlx43.doc.steam-02.jpg](/images/omlx43.doc.steam-02.jpg)

![omlx43.doc.steam-03.jpg](/images/omlx43.doc.steam-03.jpg)

### Application Menu > Games > Steam

![omlx43.doc.steam-04.jpg](/images/omlx43.doc.steam-04.jpg)

![omlx43.doc.steam-05.jpg](/images/omlx43.doc.steam-05.jpg)

![omlx43.doc.steam-06.jpg](/images/omlx43.doc.steam-06.jpg)

![omlx43.doc.steam-07.jpg](/images/omlx43.doc.steam-07.jpg)

![omlx43.doc.steam-08.jpg](/images/omlx43.doc.steam-08.jpg)

![omlx43.doc.steam-09.jpg](/images/omlx43.doc.steam-09.jpg)

![omlx43.doc.steam-10.jpg](/images/omlx43.doc.steam-10.jpg)

![omlx43.doc.steam-11.jpg](/images/omlx43.doc.steam-11.jpg)

If you have nvidia driver, you want to install also the 32bit version of the nvidia driver


`$ sudo dnf clean all;dnf clean all;dnf repolist`

then:
`$ sudo dnf install --enablerepo=rock-x86_64-non-free nvidia-32bit`
or
`$ sudo dnf install --enablerepo=rock-x86_64-non-free nvidia-legacy-32bit`










