---
title: Comment se connecter à Internet en mode console ou en mode récupération ?
description: 
published: true
date: 2021-09-26T21:29:39.480Z
tags: documentation, tutoriel, guide d'utilisateur
editor: markdown
dateCreated: 2020-07-07T08:04:15.837Z
---

# Comment se connecter à Internet en mode console ou en mode récupération ?


> Note : Ce tutoriel suppose que l'utilisateur dispose d'un système où Internet fonctionnait correctement jusqu'à ce que quelque chose se passe mal.
{.is-info}


Il peut arriver que vous deviez démarrer en mode console ou en mode de récupération au lieu du bureau Plasma pour effectuer des opérations de maintenance ou de réparation.

![boot-advanced.jpg](/images/boot-advanced.jpg)

![boot-console-mode.jpg](/images/boot-console-mode.jpg)

![boot-recovery-mode.jpg](/images/boot-recovery-mode.jpg)


Il est possible que le wifi ne fonctionne pas dans ces modes.

## Wifi
Pour se connecter au wifi à partir de la ligne de commande, il faut utiliser la commande `nmcli`. Exemple :

Pour déterminer l'appareil à connecter, exécutez la commande suivante :

```
$ nmcli dev status
```

Cette commande énumère tous les périphériques réseau disponibles. Dans cet exemple, nous savons que nous sommes en wifi mais pas wifi-p2p et la commande liste le périphérique wifi comme étant wlp4s0, donc pour se connecter :

```
$ nmcli --ask dev con wlp4s0
```

Il devrait vous demander votre mot de passe wifi, puis connecter votre wifi.
Vous pouvez maintenant effectuer les opérations de maintenance ou les réparations qui nécessitent un accès à l'internet.

## Connexion Ethernet

Si vous utilisez une connexion Ethernet, la procédure de connexion est pratiquement la même :

```
$ nmcli dev status
```

Si votre périphérique Ethernet est listé par exemple comme elp4s0 :

```
$ nmcli dev con elp4s0
```

L'option `--ask` n'est normalement pas nécessaire, car votre système a déjà la permission de le faire.
Les permissions wifi sont normalement séparées et uniques des permissions système.

\-




