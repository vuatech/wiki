---
title: Jak połączyć się z Internetem w trybie konsoli lub trybie odzyskiwania?
description: 
published: true
date: 2021-09-26T21:29:39.480Z
tags: dokumentacja, howto, podręcznik użytkownika
editor: markdown
dateCreated: 2020-07-07T08:04:15.837Z
---

# Jak połączyć się z Internetem w trybie konsoli lub trybie odzyskiwania?


> Uwaga: Ten poradnik zakłada, że użytkownik ma system, w którym internet działał poprawnie, dopóki coś nie poszło nie tak.
{.is-info}


Czasami może być konieczne uruchomienie systemu w trybie konsoli lub trybie odzyskiwania zamiast w trybie pulpitu Plasma w celu przeprowadzenia konserwacji lub naprawy.

![boot-advanced.jpg](/images/boot-advanced.jpg)

![boot-console-mode.jpg](/images/boot-console-mode.jpg)

![boot-recovery-mode.jpg](/images/boot-recovery-mode.jpg)


Może się okazać, że Wi-Fi nie działa w tych trybach .

## Wifi
Aby połączyć się z wifi z linii poleceń należy użyć komendy `nmcli`. Przykład:

Aby określić, które urządzenie ma zostać podłączone, wydaj polecenie:

```
$ nmcli dev status
```

Spowoduje to wyświetlenie wszystkich dostępnych urządzeń sieciowych. W tym przykładzie wiemy, że mamy wifi, ale nie jest to wifi-p2p, a polecenie wyświetla urządzenie wifi jako wlp4s0, więc aby się połączyć:

```
$ nmcli --ask dev con wlp4s0
```

Powinien wyświetlić się monit o hasło Wi-Fi, a następnie połączyć się z siecią Wi-Fi. Teraz możesz wykonywać wszelkie prace konserwacyjne lub naprawy wymagające dostępu do Internetu.

## Połączenie ethernet 

Jeśli korzystasz z połączenia ethernetowego, połączenie jest w zasadzie takie samo:

```
$ nmcli dev status
```

Jeśli urządzenie Ethernet jest wymienione jako przykład jako elp4s0:

```
$ nmcli dev con elp4s0
```

Opcja `--ask` nie jest zwykle potrzebna, ponieważ system ma już do tego uprawnienia.
Uprawnienia Wi-Fi są zwykle oddzielne i unikalne od uprawnień systemowych.

\-




