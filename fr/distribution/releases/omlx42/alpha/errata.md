---
title: OpenMandriva Lx 4.2 Alpha Errata
description: 
published: true
date: 2021-09-26T20:55:57.359Z
tags: 4.2
editor: markdown
dateCreated: 2020-02-27T16:13:04.324Z
---

# OpenMandriva Lx 4.2 Alpha Errata - Dysfonctionnements connus
> Comme pour toute version, il reste des problèmes et des bogues qui peuvent ne pas avoir été résolus. Cette page documente ceux qui peuvent causer des désagréments et, dans la mesure du possible, détaille comment ils peuvent être résolus.
{.is-info}


**Il est recommandé de lire les dernières** [notes de mise à jour].(https://wiki.openmandriva.org/en/releases/omlx42/alpha/notes) **sur notre wiki**.

## Cartes graphiques NVIDIA
Cette version inclut le pilote nouveau, issu de l'ingénierie inverse, qui offre un support modérément bon pour la plupart des cartes NVIDIA. Pour certains travaux sur deux écrans, il est plus performant que le pilote binaire de NVIDIA, car il prend en charge la rotation de l'écran sur un second moniteur, ce qui est utile pour les moniteurs dont l'écran est rotatif.
Les utilisateurs peuvent utiliser les pilotes du site web de nvidia mais ils ne sont pas supportés par OpenMandriva. Ces pilotes ne peuvent pas être pris en charge par OpenMandriva pour un certain nombre de raisons.
L'installation et la maintenance de tout pilote nVidia propriétaire relèvent de l'option et de la responsabilité exclusives de l'utilisateur.

## Disques durs SSD NVME
Il existe un problème bien connu avec certains disques durs SSD NVME (en particulier les plus récents) et les périphériques PCIE où le SSD peut ne pas être reconnu. Pour notre ISO *Live*, il existe une solution de contournement décrite dans les [notes de version](/releases/omlx41/notes).
Le problème est connu et fait l'objet de travaux par les développeurs d'OpenMandriva et les développeurs en amont.
La reconnaissance matérielle des disques SSD nvme devrait être considérablement améliorée. 
Il est connu que certains SSD Samsung nvme qui n'étaient pas reconnus auparavant le sont maintenant avec cette version du noyau. Ce problème est bien sûr très spécifique au matériel.

Sur un système installé, l'utilisateur peut souhaiter ajouter cette correction à `/etc/default/grub` et lancer `update-grub2` pour rendre la correction globale. Vous devriez utiliser celui que vous avez constaté comme fonctionnel sur l'ISO *Live*.

Si `(PCIE ASPM=OFF)` a fonctionné pour vous, ajoutez :
`pcie=aspm=off`
aux lignes :
`GRUB_DECLINE_LINUX_DEFAULT`
`GRUB_DECLINE_LINUX_RECOVERY`
dans 
`/etc/default/grub` 
puis exécutez :
`$ sudo update-grub2`

Si `(NVME APST=OFF)` fonctionne, ajoutez à la place :
`nvme_core.default_ps_max_latency_us=0`

Comme toujours, les utilisateurs sont encouragés à poser des questions sur tout ce qu'ils ne comprennent pas sur notre [forum] (https://forum.openmandriva.org/).

## GEOIP
Le réglage automatique du GEOIP par l'installateur peut ne pas définir correctement le fuseau horaire.

## Comment configurer l'imprimante
Allumer l'imprimante et vérifier si elle est configurée automatiquement. Vérifiez si le bon pilote a été installé. Si l'imprimante a été configurée automatiquement et que vous avez le bon pilote, c'est parfait, vous êtes prêt.
Si ce n'est pas le cas, éteignez votre imprimante. Ouvrez *Paramètres de l'imprimante* alias `system-config-printer` et supprimez votre imprimante.
Si le pilote correct n'a pas été installé par défaut, nous devrons ajouter un paquet de logiciels.

L'étape suivante consiste à déterminer quel logiciel ajouter à votre imprimante.

Dans OpenMandriva Lx, il s'agit très probablement d'un paquet 'task-printing' spécifique à votre marque d'imprimante. Les paquets sont les suivants :
- task-printing-canon
- task-printing-epson
- task-printing-hp
- task-printing-lexmark
- task-printing-okidata
- task-printing-misc

Installez le paquet qui correspond à votre marque ou le paquet misc si ce n'est pas le cas. Exemple avec okidata :
```
$ sudo dnf install task-printing-okidata
```
Remettez l'imprimante sous tension et elle devrait se configurer automatiquement (il est parfois nécessaire de redémarrer l'imprimante pour que la configuration automatique fonctionne).

Si ce n'est pas le cas, demandez de l'aide [ici] (https://forum.openmandriva.org/c/en/support)

## Discover
En ce qui concerne les logiciels dans les dépôts, Discover peut ne pas afficher tous les paquets disponibles.
Cela est dû au fait que son cache n'a pas été vidé et que la liste des dépôts n'a pas été récupérée au premier démarrage.
La solution est la suivante : exécutez les commandes
```
$ sudo rm -rf /var/cache/PackageKit/* /var/cache/app-info/*
$ sudo pkcon refresh force
```
Si vous souhaitez explorer d'autres dépôts, vous devez les activer à l'aide de [Software Repository Selector] (/fr/doc/repositories-tldr) et rafraîchir à nouveau le cache.

## Multiboot
Dans le « monde réel », le multiboot fonctionne bien la plupart du temps, mais lorsqu'il y a des problèmes, la solution est parfois une méthode de dépannage plutôt qu'un correctif. Ce ne sont que les réalités du multiboot.

Il n'est pas non plus possible pour OpenMandriva QA de tester notre chargeur de démarrage avec tous les types de systèmes de fichiers sur toutes les distributions Linux, ni même sur le « Top 10 » des distributions Linux. Le fait est que, que ce soit pour le multi-boot avec Windows ou d'autres distros Linux, nous nous appuyons exclusivement sur les rapports des utilisateurs pour savoir ce qui fonctionne et ce qui ne fonctionne pas en matière de multi-boot. 

Un problème connu rencontré avec OM Lx bootloader est que OM Lx grub2 ne crée pas d'entrées de démarrage pour les systèmes openSUSE qui utilisent le système de fichiers btrfs. OM Lx grub2 fonctionne avec les systèmes openSUSE qui utilisent le système de fichiers ext4.
Ceci est dû au fait qu'openSUSE utilise une syntaxe personnalisée pour ses correctifs btrfs pour les paquets openSUSE os-prober et grub2 qui ne sont pas compatibles avec le code OM Lx. On ne sait pas encore si le bootloader OM Lx fonctionne ou non avec openSUSE avec d'autres types de systèmes de fichiers tels que XFS ou F2FS.

La solution consiste pour les utilisateurs à changer de chargeur de démarrage dans les paramètres du firmware UEFI ou du BIOS.
L'alternative peut être d'utiliser le chargeur de démarrage openSUSE s'il reconnaît votre système OpenMandriva.
Au fur et à mesure que les utilisateurs signalent des problèmes liés au multiboot, nous corrigeons ce qui peut l'être. Les problèmes que nous ne pouvons pas résoudre seront signalés dans les Errata de nos versions OM Lx.

## Problèmes connus en cours de traitement

Notre système de suivi des bogues a connu quelques problèmes et nous demandons donc que les nouveaux rapports de bogues soient déposés sur notre [Forum](https://forum.openmandriva.org/) ou 
sur [Github Issues](https://github.com/OpenMandrivaAssociation/OpenMandrivaAssociation.github.io/issues)

Bugs déposés sur OpenMandriva Issue Tracker :

- [Cooker Host : VirtualBox 6.1.12 VM's ne démarre pas](https://issues.openmandriva.org/show_bug.cgi?id=2634)

- [VBox bureau plasma plante (virtualbox-guest-additions)](https://issues.openmandriva.org/show_bug.cgi?id=2633)

- [Pas de son à l'ouverture de session (ou son anormal) Plasma 5.19.3, KF 5.72.0](https://issues.openmandriva.org/show_bug.cgi?id=2629)

- [Les changements de points de montage dans KDE Partition Manager ne sont pas écrits dans /etc/fstab (TOUTES les versions d'OM Lx)](https://issues.openmandriva.org/show_bug.cgi?id=2628)

- [OM-Control-Center, centre de controle OM, ne fonctionne pas avec Wayland (Cooker)](https://issues.openmandriva.org/show_bug.cgi?id=2625)

- [Échec de la mise à niveau du noyau d'une branche à une autre branche de même numéro de version](https://issues.openmandriva.org/show_bug.cgi?id=2619)

- [grub2-editor (kcm_grub2) "Echec de l'enregistrement des paramètres GRUB." DBus backend error. (TOUTES les versions d'OM Lx)](https://issues.openmandriva.org/show_bug.cgi?id=2618)

- [Samba ne marche pas](https://issues.openmandriva.org/show_bug.cgi?id=2609)

Bugs déposés sur Github Issues :

- [L'utilisateur doit saisir deux fois le mot de passe pour le wifi (NM applet cassé) #53](https://github.com/OpenMandrivaAssociation/OpenMandrivaAssociation.github.io/issues/53)


