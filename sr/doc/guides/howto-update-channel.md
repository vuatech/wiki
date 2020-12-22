---
title: Како надоградити канал
description: 
published: true
date: 2020-04-28T09:09:45.491Z
tags: документација, како да, корисничко упуство, напредно
---

# Како надоградити канал
## Како урадити надоградњу са Rock на Rolling

Новим корисницима OpenMandriva Lx-а ми предлажемо да почну са Rock стабилним издањем да би научили ако систем ради а затим, уколико то желе, пређу на Rolling.

Корисник 'Rolling' издања би требало да зна да користи командну и да зна основе [dnf](/en/doc/using-dnf) менаџера пакета.
Такође корисник мора да прочита и разуме  [План објављивања OpenMandrivе и репозиторијума](/en/doc/release-plan-and-repositories).

За надоградњу на Rolling:

- Изборник репозиторијума Отвореног софтвера (`om-repo-picker`) 

Мени Апликације > Изборник репозиторијума Софтвера

![repositories01.jpg](/images/repositories01.jpg)

Такође можете изабрати OpenMandriva изборник репозиторијума у OM Welcome

![repositories07.jpg](/images/repositories07.jpg)

- Иди на први избор 'Надоградња канала'

![repositories02.jpg](/images/repositories02.jpg)

- Изаберите 'Rolling' са падајућег менија

![update-channel-rolling.jpg](/images/update-channel-rolling.jpg)

потврдите кликом на У реду и унесите своју root лозинку када буде затражена. Ово може потрајати па будите стрпљиви.

Овом поступком сте сада променили репозиторијуме са са Rock на Rolling издање па ће требати да урадите надоградњу система (`distro-sync`)

- Да би надоградили систем отворите конзолу и покрените команде:
```
$ sudo dnf clean all ; dnf clean all
$ sudo dnf --allowerasing distro-sync
```

\-
