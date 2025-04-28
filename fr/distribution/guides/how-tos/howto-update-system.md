---
title: Comment mettre à jour le système
description: Comment mettre à jour votre système Rock ou Rolling
published: true
date: 2025-04-22T21:45:09.294Z
tags: documentation, howto, user-guide
editor: markdown
dateCreated: 2021-02-19T15:43:53.051Z
---

# Comment mettre à jour le système

> La procédure d'OpenMandriva concernant la mise à niveau du système est différente.
> Ne **pas** utiliser Discover pour la mise à niveau du système.
{.is-danger}

<br>

## Comment mettre à jour Rock
- Pour mettre à jour votre système Rock, ouvrez Konsole et exécutez les commandes suivantes :
```
$ sudo dnf clean all ; dnf clean all ; dnf repolist
$ sudo dnf upgrade
```



<br>

## Comment mettre à jour ROME
- Pour mettre à jour ROME, votre système rolling, ouvrez Konsole et exécutez les commandes suivantes :
```
$ sudo dnf clean all ; dnf clean all ; dnf repolist
$ sudo dnf distro-sync --allowerasing
```

- ou

![update-menu.png](/images/update-menu.png)


- ou

![update-60-taskmanager02.jpg](/images/update-60-taskmanager02.jpg)

- ou

![update-dnfdrake.png](/images/update-dnfdrake.png)
