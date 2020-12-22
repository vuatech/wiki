---
title: Како инсталирати Steam на OpenMandriva
description: 
published: true
date: 2020-04-10T19:38:50.429Z
tags: 
---

# Како инсталирати Steam на OpenMandriva


## За инсталацију Steam-а на OpenMandriva Lx треба предузети следеће кораке:

### Покрените Изборник Репозиторијума за Софтвер
- из менија Апликације

![install-steam-01.jpg](/images/install-steam-01.jpg)

- или из OM Добродошли

![repositories07.jpg](/images/repositories07.jpg)

### Активирајте `/main 32bit` репозиторијум

![install-steam-02.jpg](/images/install-steam-02.jpg)

### као и `/non-free` репозиторум

![install-steam-03.jpg](/images/install-steam-03.jpg)

Кликните <kbd>У реду</kbd> за примену

> Бићете упитани за root лозинку
{.is-warning}


![install-steam-04.jpg](/images/install-steam-04.jpg)

### Када завршите са вашим изменама, покрените следећу команду у конзоли
```
$ sudo dnf clean all ; dnf clean all ; dnf repolist
```

![install-steam-05.jpg](/images/install-steam-05.jpg)

### Инстлирај Steam

```
$ sudo dnf --refresh install steam
```

![install-steam-06.jpg](/images/install-steam-06.jpg)

![install-steam-07.jpg](/images/install-steam-07.jpg)

![install-steam-08.jpg](/images/install-steam-08.jpg)

### Мени Апликације > Игрице > Steam

![install-steam-09.jpg](/images/install-steam-09.jpg)

![install-steam-10.jpg](/images/install-steam-10.jpg)

![install-steam-11.jpg](/images/install-steam-11.jpg)

![install-steam-12.jpg](/images/install-steam-12.jpg)

![install-steam-13.jpg](/images/install-steam-13.jpg)

