---
title: Како решити најчешће узроке нетачног времена у двосистемском окружењу са windows системима
description: 
published: true
date: 2020-04-10T19:38:49.139Z
tags: 
---

# Како решити најчешће узроке нетачног времена у двосистемском окружењу са windows системима

Уколико имате проблем са нетачним временом у Линуксу са двоструким стартовањем са windows системом, 

### Проверите ваш Линукс систем:
```
$ timedatectl
                      Локално време: Tue 2018-08-21 13:11:23 CDT
                  Универзално време: Tue 2018-08-21 18:11:23 UTC
                        RTC време: Tue 2018-08-21 18:11:23
                       Временска зона: US/Central (CDT, -0500)
       Системски часовник синхронизован: не
systemd-timesyncd.service активан: Да
                 RTC у локалном TZ: не
```

Погледајте последњу линију. Уколико је `RTC у локалном TZ: да` успешно сте подесили, и проблем је на неком другом месту.
Али највероватније је да ћете видети локални TZ подешен на не.

### Да би то исправили покрените команду:

```
$ sudo timedatectl set-local-rtc 1 --adjust-system-clock
```

> Бићете упитани за root лозинку, и команда ће бити извршена.
{.is-warning}


Да би проверили, поново укуцајте:
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

Ово је исправно.
*(Упозорење се може игнорисати)*
<br>

### Дефиниције:

`RTC` = Real Time Часовник се такође назива хардверски часовник или hwclock
`TZ` = Временска Зона