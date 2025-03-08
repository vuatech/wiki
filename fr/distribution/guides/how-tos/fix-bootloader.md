---
title: Comment réparer un chargeur de démarrage cassé
description: 
published: true
date: 2022-04-02T16:07:14.522Z
tags: documentation, tutoriel, guide d'utilisateur
editor: markdown
dateCreated: 2020-09-10T21:59:11.289Z
---

# Comment réparer un chargeur de démarrage cassé

OpenMandriva Lx utilise le chargeur de démarrage grub2, nous utilisons donc les commandes grub2.
La commande pour examiner l'ordinateur et écrire le menu complet de grub2 est la suivante :
```
$ sudo grub2-mkconfig -o /boot/grub2/grub.cfg
```
Dans la plupart des cas, cette commande plus simple fonctionnera :
```
$ sudo update-grub2
```
Ensuite, pour installer le chargeur de démarrage grub2 sur le disque à partir duquel vous souhaitez démarrer :
```
$ sudo grub2-install /dev/xxx
```
Vous remplacerez le « *xxx* » par le nom du disque sur lequel vous voulez ou avez démarré OMLx, comme `sda` ou si c'est un disque nvme quelque chose comme `nvme0n1`.

Pour ce faire, vous devez évidemment avoir accès à votre système OMLx. Si vous n'y avez pas facilement accès, vous pouvez essayer [Rescatux](https://sourceforge.net/p/rescatux/) ou [Super Grub2 Disk](https://sourceforge.net/p/supergrub2/). Pour cette tâche, vous pouvez essayer Super Grub2 Disk en premier.

Pour connaître le nom de vos périphériques de stockage ou de vos lecteurs, l'utilisateur peut simplement ouvrir le Gestionnaire de partitions de KDE ou, à partir de Konsole, lancer la commande :
```
$ sudo fdisk -l
```
<br>

### Informations complémentaires :
Les commandes `grub2-mkconfig` et `update-grub2` utilisent l'utilitaire appelé 'os-prober' pour rechercher d'autres systèmes d'exploitation sur l'ordinateur.
L'utilisateur peut lancer cette commande indépendamment pour voir si os-prober reconnaît correctement tous les autres systèmes d'exploitation sur l'ordinateur de l'utilisateur. Comme ceci :
```
$ sudo os-prober
```

<br>

### Lectures utiles
[Manuel Grub2](https://www.gnu.org/software/grub/manual/grub/html_node/index.html)
[Comment restaurer un GRUB 2 qui ne démarre pas sous Linux](https://www.linux.com/training-tutorials/how-rescue-non-booting-grub-2-linux/)
Quelques pages de manuel : [1](https://aty.sdsu.edu/bibliog/latex/debian/grub2rescue.html) [2](https://www.gnu.org/software/grub/manual/grub/html_node/GRUB-only-offers-a-rescue-shell.html)



