---
title: How to solve the most common cause of incorrect time in dual boot with windows systems
description: 
published: true
date: 2020-03-13T12:12:49.510Z
tags: documentation, howto, user-guide, troubleshooting
---

# How to solve the most common cause of incorrect time in dual boot with windows systems

If you have an incorrect time issue in Linux on a dual boot with windows system,

### Check your Linux system:
```
$ timedatectl
                      Local time: Tue 2018-08-21 13:11:23 CDT
                  Universal time: Tue 2018-08-21 18:11:23 UTC
                        RTC time: Tue 2018-08-21 18:11:23
                       Time zone: US/Central (CDT, -0500)
       System clock synchronized: no
systemd-timesyncd.service active: yes
                 RTC in local TZ: no
```

Look at the last line. If it is: `RTC in local TZ: yes` you are set correctly, and the problem must be elsewhere.
But most likely you will see local TZ is set to no.

### To fix it run command:

```
$ sudo timedatectl set-local-rtc 1 --adjust-system-clock
```

> You will be asked for root password, and the command will be executed.
{.is-warning}


To verify, type again:
```
$ timedatectl
                      Local time: Tue 2018-08-21 18:15:28 CDT
                  Universal time: Tue 2018-08-21 23:15:28 UTC
                        RTC time: Tue 2018-08-21 18:15:28
                       Time zone: US/Central (CDT, -0500)
       System clock synchronized: no
systemd-timesyncd.service active: yes
                 RTC in local TZ: yes

Warning: The system is configured to read the RTC time in the local time zone.
         This mode cannot be fully supported. It will create various problems
         with time zone changes and daylight saving time adjustments. The RTC
         time is never updated, it relies on external facilities to maintain it.
         If at all possible, use RTC in UTC by calling
         'timedatectl set-local-rtc 0'.
```

This is correct.
*(The warning can be ignored)*
<br>

### Definitions:

`RTC` = Real Time Clock also called hardware clock or hwclock
`TZ` = Time Zone