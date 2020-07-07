---
title: How to connect to internet in console mode or recovery mode
description: 
published: true
date: 2020-07-07T08:04:15.837Z
tags: documentation, howto, user-guide
editor: markdown
---

# How to connect to internet in console mode or recovery mode


> Note: This how-to assumes that user has a system where internet was working properly until something went wrong.
{.is-info}


Sometimes you may need to boot in to console mode or recovery mode instead of Plasma desktop in order to do maintenance or repair.

![boot-advanced.jpg](/images/boot-advanced.jpg)

![boot-console-mode.jpg](/images/boot-console-mode.jpg)

![boot-recovery-mode.jpg](/images/boot-recovery-mode.jpg)


You may find that wifi does not work in these modes.

## Wifi
To connect to wifi from command line you use the `nmcli` command. Example:

To determine what device to connect run this command:

```
$ nmcli dev status
```

This will list any available network devices. In this example we know that we are wifi but not wifi-p2p and the command lists wifi device as wlp4s0, so to connect:

```
$ nmcli --ask dev con wlp4s0
```

This should ask for your wifi password and then connect your wifi.
Now you can do any maintenance or repairs that require internet access.

## Ethernet connection

If you are using ethernet connection, to connect is basically the same:

```
$ nmcli dev status
```

If your ethernet device is listed as an example as elp4s0:

```
$ nmcli dev con elp4s0
```

The `--ask` option is not normally needed, as your system already has permission for this.
Wifi permissions are normally separate and unique from system permissions.

\-




