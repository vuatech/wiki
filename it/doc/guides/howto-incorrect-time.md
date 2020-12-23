---
title: Come correggere la causa più comune di orario diverso in situazione di dual boot con sistema Windows
description: 
published: true
date: 2020-12-21T23:54:01.434Z
tags: 
editor: undefined
dateCreated: 2020-05-02T22:15:51.459Z
---

# Come correggere la causa più comune di orario diverso in situazione di dual boot con sistema Windows

Se hai il problema di avere l'orario inesatto su Linux in dual boot con Windows

### Controlla il tuo sistema Linux:
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

Guarda l'ultima riga. Se dice: `RTC in local TZ: yes` sei a posto e il problema deve risiedere altrove.
Ma probabilmente vedrai local TZ impostato a no.

### Per risolvere digita questo comando:

```
$ sudo timedatectl set-local-rtc 1 --adjust-system-clock
```

> Ti verrà chiesta la password di root e il comando verrà eseguito
{.is-warning}


Per verificare digita ancora:
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

Così è corretto
*(Il messaggio di warning può essere ignorato)*
<br>

### Definizioni:

`RTC` = real-time clock - orologio in tempo reale detto anche orario hardware o hwclock
`TZ` = Time Zone (Fuso Orario)

\-
