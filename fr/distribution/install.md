---
title: Installer OpenMandriva Lx
description: 
published: true
date: 2025-04-30T09:48:16.196Z
tags: 
editor: markdown
dateCreated: 2021-10-02T20:03:48.871Z
---

***Si vous avez des questions avant d'installer OpenMandriva Lx, veuillez nous contacter à partir de [OpenMandriva Chat](https://wiki.openmandriva.org/en/team/chat) ou sur le [Forum d'assistance OpenMandriva](https://forum.openmandriva.org/c/support/17).*** Les personnes peuvent se trouver dans des fuseaux horaires différents, veuillez donc nous laisser le temps de vous répondre.

# 1\. Transférer l'image téléchargée sur une clé USB

Pour transférer l'image live/installation sur un périphérique de stockage USB, vous pouvez utiliser :
om-imagewriter, KDE isoimagewriter, SUSE Studio ImageWriter, ligne de commande dd.

*Utilisateurs de Windows :*
Si vous utilisez d'autres outils d'écriture usb comme certains outils Windows (par exemple Rufus), vous devez sélectionner le mode `dd`, sinon le nom du volume sera tronqué et le processus de démarrage sera interrompu.
Balena Etcher fonctionne bien pour transférer les images ISO d'OpenMandriva vers un périphérique de stockage USB.

# 2\. Démarrage à partir d'une clé USB

La plupart des ordinateurs démarrent automatiquement à partir d'une clé USB. Il suffit de l'insérer et d'allumer votre ordinateur ou de le redémarrer. Un menu devrait s'afficher, vous invitant à choisir les différentes entrées.

Si votre ordinateur ne démarre pas automatiquement à partir de la clé USB, essayez de maintenir la touche F12 enfoncée lors du premier démarrage ou ESC. Sur la plupart des machines, cela vous permettra de sélectionner le périphérique USB à partir d'un menu de démarrage spécifique au système.

F12 et ESC sont les touches les plus courantes pour faire apparaître le menu de démarrage de votre système, mais F2 et F10 sont des alternatives courantes. Si vous n'êtes pas sûr de vous, recherchez un bref message au démarrage de votre système : il vous indiquera souvent la touche sur laquelle appuyer pour faire apparaître le menu de démarrage.

Essayez de trouver la bonne touche sur Internet, ou n'hésitez pas à demander de l'aide sur notre forum ou notre salon de discussion.

## Démarrage à partir d'un DVD
Le démarrage à partir d'un DVD est obsolète.

# 3\. Démarrer OpenMandriva Lx en mode live

Il vous sera d'abord demandé de démarrer le mode « Live ». Celui-ci démarre automatiquement au bout de 30 secondes. Le mode Live peut être utilisé pour tester la distribution sans toucher à l'espace disque, ou pour installer la distribution.

![1](https://forum.openmandriva.org/uploads/default/optimized/2X/8/8c9727b79d2d14b3bbd0855fd324602ed1b3ff8f_2_690x283.jpeg)

À partir de ce menu, vous pouvez changer la langue et la disposition du clavier. Cela n'a aucune incidence sur la disposition du clavier et la langue de l'installation proprement dite, qui seront demandées ultérieurement. 
 

![2](https://forum.openmandriva.org/uploads/default/optimized/2X/5/542eb029a442b16f20ddabc2b689789badd39332_2_690x322.jpeg)

Veuillez noter que la disposition du clavier par défaut du mode « live » est US QWERTY, ce qui peut s'avérer délicat si vous souhaitez définir un mot de passe utilisateur pour l'installation sans vérifier les caractères. Le nombre de langues et de dispositions pour le mode « live » est très limité pour le mode, mais il y a beaucoup plus de choix lors de l'installation proprement dite plus tard.

![3](https://forum.openmandriva.org/uploads/default/optimized/2X/d/dc104372eed37891b803654bbe9af53fcc7dc844_2_690x322.png)

# 4\. Bienvenue dans le mode live d'OpenMandriva Lx

![image](https://forum.openmandriva.org/uploads/default/optimized/2X/f/f834e3ba9e2380e64bdfdaa6cdb2a0f85a22905e_2_667x500.jpeg)

vous pouvez en toute sécurité fermer ou réduire la fenêtre d'accueil pour afficher les icônes du bureau.

Lorsque vous vous sentez prêt pour l'installation, cliquez sur l'icône « installer OpenMandriva Lx ».

![image](https://forum.openmandriva.org/uploads/default/original/2X/1/152f47602da6aaec3baade2c95341ae57837247d.png)

# 5\. Préparation de l'installation

Choisissez d'abord votre langue et cliquez sur suivant.

![6](https://forum.openmandriva.org/uploads/default/optimized/2X/3/3ec3e0ddc0ad5c6b95d95814d54f7bd6268555ce_2_690x369.png)

Choisissez ensuite votre fuseau horaire en fonction de cette [liste](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones#List) soit en cliquant sur la carte, soit en utilisant le menu. Vérifiez ensuite que la langue, les chiffres et les dates sont correctement définis et cliquez sur suivant.

![7](https://forum.openmandriva.org/uploads/default/optimized/2X/b/b012db7a20f89cf37474ab6b36e4476b50e1aa01_2_690x369.jpeg)

Il vous sera d'abord demandé de sélectionner votre disposition de clavier. Si le programme d'installation ne détecte pas correctement la disposition par défaut, vous pouvez la modifier et la vérifier à l'aide du champ « Tester la disposition du clavier ».

![8](https://forum.openmandriva.org/uploads/default/optimized/2X/6/6ffe4b3c63507fb964e06fb3679893997180bf63_2_690x369.png)

C'est ici qu'intervient le moment le plus important de l'installation, puisqu'il s'agit de savoir comment le système sera installé sur votre disque dur. Selon que vous avez déjà un ou plusieurs systèmes d'exploitation installés sur votre disque, Calamares peut vous proposer :

Certaines options automatisées :

-   Réduire une partition existante et installer OpenMandriva Lx avec tout autre système d'exploitation déjà disponible sur votre système. Si vous avez une partition Windows, c'est l'option que vous pouvez choisir pour conserver ce système d'exploitation. (recommandé pour les débutants)
-   Utiliser une partition existante et remplacer tous les fichiers et/ou le système d'exploitation sur cette partition par une nouvelle installation d'OpenMandriva Lx. (utilisateurs avancés)
-   Utiliser le disque entier et créer une partition où tout sera installé sous root (administrateur ou super utilisateur), toutes les autres partitions seront supprimées. (débutants)

Option manuelle :

-   Cette méthode vous donne la liberté de définir n'importe quelle option, n'importe quel système de fichiers et n'importe quelle table de partition, mais elle vous laisse la possibilité de casser complètement l'installation. Assurez-vous de savoir ce que vous faites. Une autre page sera créée pour le partitionnement avancé. (utilisateurs experts)

En plus de l'option sélectionnée, il y a une option pour le fichier d'échange (il y aura un fil dédié au fichier d'échange). À moins que vous ne sachiez ce que vous faites, Swap to file est une bonne option. 
 

![image](https://forum.openmandriva.org/uploads/default/optimized/2X/4/438b7613cbcc876b9baa212e0300071490d70ce7_2_690x143.png)

Cochez l'option « crypter le système » si vous souhaitez ajouter une couche de sécurité à vos données. Le système vous demandera le mot de passe saisi à chaque fois que vous démarrerez le système.

![image](https://forum.openmandriva.org/uploads/default/optimized/2X/d/d0cf1db41fef4319988fa69e1e11154479761477_2_690x163.png)

Créez un compte d'utilisateur, donnez un nom à votre ordinateur et donnez un mot de passe administrateur (aussi appelé mot de passe root) ou cocher « utiliser le même mot de passe pour le compte administrateur ».

![image](https://forum.openmandriva.org/uploads/default/optimized/2X/e/e46e539f893a10323d4c7bef786ac4d49807fd9f_2_690x349.png)

Après avoir vérifié le résumé de l'installation, vous pouvez cliquer sur « Installer ».

![image](https://forum.openmandriva.org/uploads/default/optimized/2X/9/92932b3faacc4819d5120defad361a7722d3be59_2_690x455.png)

Attendez la fin du processus d'installation.

![image](https://forum.openmandriva.org/uploads/default/optimized/2X/d/dd3cb650845245a372d776b1eade5b8763fc7158_2_690x455.jpeg)

Une fois cela fait, cliquez sur Terminé et redémarrez votre ordinateur (vous pouvez également cocher « Redémarrer maintenant »).

![image](https://forum.openmandriva.org/uploads/default/optimized/2X/8/8d89ea930a3998a90533d7cedb6b354d8840725d_2_690x455.png)

Une fois que votre ordinateur a redémarré, vous pouvez utiliser OpenMandriva Lx.

# Notes

[Source originale (forum)](https://forum.openmandriva.org/t/h/4223)

Lire également :
* [Comment créer une partition root, home et swap lors de l'installation ?](/en/distribution/guides/how-tos/howto-root-home-swap)
* [Comment obtenir une liste de tous les paquets inclus dans isos ?](/en/distribution/guides/how-tos/list-packages-iso)
