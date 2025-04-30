---
title: Notes de version OpenMandriva Lx 6.0
description: 
published: true
date: 2025-03-14T11:26:15.121Z
tags: 6.0
editor: markdown
dateCreated: 2025-03-10T19:02:54.601Z
---

# Notes de version OpenMandriva Lx 6.0

Les équipes d'OpenMandriva ont le plaisir d'annoncer la disponibilité de l'édition **OpenMandriva Lx 6.0 Rock**.
<br>

## Médias disponibles
Cette version est disponible sous la forme d'une clé Live USB amorçable (memory stick), téléchargeable au format ISO.
Elles sont disponibles sur notre page [téléchargements](https://www.openmandriva.org/release-picking).
L'installation sur une clé USB est généralement très rapide. Comme toujours, la vitesse dépend de nombreux facteurs.
Les Live Media vous permettent d'exécuter OpenMandriva Lx directement à partir d'une clé USB (voir ci-dessous) et de l'essayer avant de l'installer.
Vous pouvez également installer le système sur le disque dur à partir de l'image en cours d'exécution ou du gestionnaire de démarrage.

**Fichiers ISO disponibles :**
- *Bureau KDE Plasma x86_64* complet (comprend les fonctionnalités les plus courantes, les logiciels multimédias et de bureautique).
- *Bureau KDE Plasma znver1*: est destinée aux processeurs AMD (plus récents que 2017), notamment aux processeurs AMD actuels (Ryzen, ThreadRipper, EPYC), qui surpasse la version générique (x86_64) en tirant parti des nouvelles fonctionnalités de ces processeurs. znver1 est destinée aux processeurs listés (Ryzen, ThreadRipper, EPYC) uniquement, ne l'installez pas sur d'autres matériels.

<!--Des images installables sont proposées pour les Pinebook Pro, Raspberry Pi 4B, Raspberry Pi 3B+, Synquacer, Cubox Pulse et les périphériques génériques compatibles UEFI (tels que la plupart des cartes serveur aarch64)-->
<br>

## Configuration requise
OpenMandriva 6.0 nécessite au moins 2048 Mo de mémoire et au moins 10 Go d'espace sur le disque dur (voir ci-dessous les problèmes connus de partitionnement). 20 Go sont recommandés pour une installation complète du bureau Plasma.

*Matériel graphique :*
Le bureau KDE Plasma nécessite une carte graphique 3D qui supporte OpenGL 2.0 ou plus. Nous recommandons l'utilisation de puces graphiques AMD, Intel, Adreno ou VC4.
<br>

## Connexion Internet
L'installateur Calamares vérifie si une connexion Internet est disponible, mais OpenMandriva 6.0 s'installera très bien même sans connexion. Il est tout à fait possible de procéder à l'installation comme vous le feriez normalement et d'utiliser votre nouveau système comme à l'accoutumée. La mise à jour d'un tel système nécessiterait d'être temporairement connecté à l'internet ou de télécharger les paquets ailleurs, de les transférer sur le système installé et d'installer les paquets mis à jour. Mais comme vous n'êtes pas connecté à l'internet, vous pouvez simplement utiliser le système et ne pas le mettre à jour pendant la durée qui vous convient.
<br>

## Machines virtuelles
À l'heure actuelle, les seuls logiciels de virtualisation sur lesquels les ISO d'OpenMandriva 6.0 sont testés sont qemu et VirtualBox. Les mêmes exigences matérielles s'appliquent lors de l'exécution dans des machines virtuelles. Pour VirtualBox, vous devez toujours avoir au moins 2048 Mo de mémoire, sinon OpenMandriva 6.0 ne démarrera pas. De même, pour VirtualBox, il est conseillé d'installer sur une nouvelle machine virtuelle, car essayer d'installer sur une machine existante peut parfois échouer.
Les images d'installation les plus récentes peuvent nécessiter la configuration du contrôleur graphique VMSVGA pour s'afficher correctement et démarrer correctement dans VirtualBox.
<br>

## Installateur Calamares
Calamares est un framework d'installation. De par sa conception, il est très personnalisable afin de satisfaire une grande variété de besoins et de cas d'utilisation. Il se veut facile, utilisable, beau, pragmatique, inclusif et indépendant de la distribution. Calamares comprend une fonction de partitionnement avancée, avec un support pour les opération de partitionnement manuelles et automatisées. Il s'agit du premier programme d'installation doté d'une option automatisée “Remplacer la partition”, qui permet de réutiliser facilement une partition à plusieurs reprises pour tester une distribution. De nombreuses distributions Linux utilisent le programme d'installation Calamares et chacune a sa propre implémentation et ses propres normes. L'utilisateur peut remarquer quelques petites différences, mais cela ne signifie pas qu'il s'agit d'un bogue.
<br>

## Partitionnement
Pour l'instant, le partitionnement des configurations LVM et Raid avec l'installateur Calamares n'est pas pris en charge.

Ce qui suit s'applique au partitionnement de toutes les installations sur le matériel : si vous avez un ordinateur UEFI/EFI et que votre BIOS offre un choix lorsque vous démarrez le média d'installation entre, par exemple :

`un disque USB amovible`
`un disque USB UEFI amovible`


Vous devez choisir l'option UEFI et démarrer à partir de là. Mais sachez aussi que tous les ordinateurs ne le font pas. Certains ordinateurs dotés d'un FIRMWARE ou d'un BIOS plus spartiate ne proposeront qu'une seule option, et c'est presque toujours la bonne. Par exemple, si sur un ordinateur portable vous ne voyez pas le choix ci-dessus, ne vous inquiétez pas. *Si vous avez plusieurs disques durs activés, ils doivent tous avoir le même type de table de partition*, soit GPT, soit MBR, pour que tout fonctionne correctement. Sur les ordinateurs UEFI en situation de multi-boot avec plusieurs disques de stockage, si vous avez déjà une partition `/boot/efi` existante, vous devez l'utiliser. Le partitionneur ne créera pas une autre partition `/boot/efi` avec les drapeaux appropriés et l'installation résultera en une erreur avec aucun chargeur de démarrage installé. Ne formatez pas, mettez simplement le point de montage sur `/boot/efi` et sélectionnez le drapeau `boot`. On peut avoir plusieurs chargeurs de démarrage différents pour différents systèmes d'exploitation dans la même partition `/boot/efi`. S'il est nécessaire de changer de chargeur de démarrage, cela se fait dans les paramètres FIRMWARE ou BIOS.
<br>

## Type de système de fichiers
Dans l'installateur Calamares pour OpenMandriva 6.0, la liste des systèmes de fichiers comprend tous les systèmes de fichiers que le système d'exploitation reconnaît pour de nombreuses raisons. Cela ne signifie pas qu'il faille utiliser n'importe quel système de la liste pour la partition racine ( `/` ). `ext4` est la recommandation officielle pour la racine, `fat32` est la recommandation pour `boot/efi`. 

`btrfs`, `f2fs` et `xfs` fonctionnent dans les tests récents mais ils sont beaucoup moins souvent testés. Nous comptons sur les retours des utilisateurs pour cela. D'après les tests récents, `btrfs` n'est pas un bon choix pour les scénarios multi-boot.

**Les autres types de systèmes de fichiers de la liste ne sont pas recommandés.**

Aucune recommandation officielle n'est faite à ce jour pour les partitions de stockage ou pour une partition `/home` séparée. On s'attend à ce que les utilisateurs qui utilisent des partitions de stockage séparées ou une partition `/home` séparée sachent ce qu'ils font. Pour `/home`, la solution la plus simple est d'utiliser `ext4` (recommandé) ou n'importe quelle partition racine. 
<br>

## Modification du type de partition
Veuillez noter que Calamares ne peut pas convertir un type de partition en un autre et préserver les données de la partition.
De plus, Calamares ne prend pas en charge la lecture ou la création de ZFS en raison des licences.

> Si vous exécutez Calamares pour modifier un type de partition existant, vous devez d'abord supprimer la partition et la recréer selon le type souhaité.
{.is-danger}

<br>

## Disques SSD NVME
Les disques SSD NVME sont normalement reconnus par l'ISO Live d'OpenMandriva. Si, pour une raison quelconque, ils ne le sont pas, nous avons quelques solutions de contournement sous 'Troubleshooting' dans le menu Grub2 de l'ISO qui peuvent fonctionner. Il s'agit de (PCIE ASPM=OFF) et (NVME APST=OFF). Nous espérons que cela fonctionnera pour la plupart des matériels. Pour en savoir plus, consultez Errata/SSD NVME. Ce problème est bien sûr très spécifique au matériel.
<br>

## Support pour l'installateur et l'EFI
Cette version d'OpenMandriva 6.0 supporte le démarrage et l'installation avec et sans UEFI.

*Notez que le démarrage sécurisé n'est PAS pris en charge.*
*Notez qu'il n'est PAS recommandé de mélanger les partitions MBR et GPT.* 

Si vous souhaitez effectuer une installation EFI sur un disque MBR existant, il sera nécessaire de convertir la table de partition du disque au nouveau schéma de partitionnement GPT. Pour ce faire, vous devez utiliser l'outil gdisk. Une commande typique serait gdisk /dev/sda : la table de partition existante sera convertie en mémoire au schéma GPT. Des avertissements seront émis concernant la perte potentielle de données, le disque ne sera pas modifié tant que vous n'aurez pas écrit la table de partition en appuyant sur w. Nous vous conseillons de sauvegarder toutes les données importantes.

Il peut arriver que la conversion ne puisse pas être effectuée, généralement parce qu'il n'y a pas assez d'espace au début ou à la fin du disque pour écrire la table des partitions. Il peut être nécessaire de supprimer ou de redimensionner une partition pour créer l'espace nécessaire, gparted est votre meilleur assistant dans ces circonstances.

Il est toujours nécessaire de créer une partition `/boot/efi` pour contenir la configuration de démarrage et celle-ci doit être créée lors de l'exécution du programme d'installation de Calamares. Lorsque l'installateur arrive à l'étape du partitionnement, la partition `/` (racine) doit être supprimée et une petite partition fat32 (300 Mo) doit être créée au début du disque. La partition doit être nommée `/boot/efi` et le drapeau `boot` doit être défini. Si l'espace disque est critique, une partition plus petite peut être utilisée, mais assurez-vous de la définir comme fat32 dans Calamares, sinon l'installation échouera. Si vous ne respectez pas ces étapes, l'installation du chargeur de démarrage échouera. Par la suite, partitionnez le disque de la manière habituelle.

N'hésitez pas à partager vos expériences sur les forums afin que nous puissions améliorer cet aspect de l'installation.

Si vous installez Windows 8, 8.1, 10 ou un système d'exploitation similaire à démarrage EFI, assurez-vous par précaution que vous disposez de disques de récupération et que vous avez sauvegardé toutes les données importantes. Nos tests ont été limités avec cette configuration, mais des installations réussies ont été effectuées sans problème.
Nous serions heureux de recevoir tout commentaire à ce sujet.
<br>

## Démarrage à partir d'une clé USB
Il est possible de démarrer cette version à partir d'un périphérique de stockage USB. Pour créer le média live/installation, vous pouvez :

- Utilisez l'outil isowriter disponible dans nos dépôts :

`sudo dnf --refresh install om-imagewriter`

Il est recommandé de disposer d'une clé USB d'une capacité d'au moins 4 Go. Un stockage permanent n'est pas nécessaire. Notez que cette opération effacera tout ce qui se trouve sur votre clé USB !

>**Utilisateurs Windows** :
Si vous utilisez d'autres outils de création de clé USB, comme certains outils Windows (par exemple [Rufus](https://rufus.ie/en)), vous devez sélectionner le mode « `dd` », sinon le nom du volume sera tronqué et le processus d'amorçage sera interrompu.
Balena Etcher fonctionne bien pour effectuer le transfert des images ISO d'OpenMandriva vers un périphérique de stockage USB.
{.is-danger}

- Par l'intermédiaire de dd
Vous pouvez également utiliser dd pour transférer l'image sur votre clé USB :

`sudo dd if=<iso_name> of=<usb_drive> bs=4M conv=fdatasync status=progress`

Remplacer <iso_name> par le chemin d'accès à l'ISO et <usb_drive> par le nœud de périphérique de la clé USB, c'est-à-dire /dev/sdb.

- SUSE Studio ImageWriter et Balena Etcher ont également été testés et fonctionnent pour transférer des images ISO vers un périphérique de stockage USB.

- Ventoy n'est pas entièrement pris en charge. Dans certaines circonstances, il peut fonctionner ou non. Veuillez créer le média d'installation en choisissant l'une des méthodes suggérées ci-dessus. Voir [OMLx 6.0 Errata](/distribution/releases/omlx60/errata) pour les solutions de secours pour Ventoy.
<br>

## Installation à partir d'une clé USB
Une fois que vous avez créé votre clé USB, éteignez l'ordinateur, branchez-la sur un port USB et redémarrez.

> Il se peut que vous deviez déconnecter ou débrancher les moniteurs secondaires pour pouvoir accéder à l'écran de connexion.
{.is-warning}


Si votre ordinateur prend en charge le démarrage à partir d'un périphérique USB, choisissez le périphérique à partir duquel vous souhaitez démarrer votre ordinateur.
Pour ce faire, vous devez interrompre le processus normal de démarrage et accéder au menu BIOS en appuyant immédiatement sur la touche qui est souvent mentionnée dans le message après le démarrage de l'ordinateur.
En général, la touche correcte est `Esc`, `Del`, `F12`, `F10`, `F9` `F8`, ou une touche similaire.
Si vous n'êtes pas sûr de vous, faites une recherche sur Internet pour savoir ce que nécessite votre matériel.

Lorsque le menu s'affiche, sélectionnez l'entrée correspondant à votre clé USB.
Vous y trouverez notamment des entrées du type

`un disque USB amovible`
`un disque USB UEFI amovible`

Si vous avez un ordinateur UEFI/EFI, veillez à sélectionner celui qui mentionne « UEFI » et démarrez-le, sinon le programme d'installation de Calamares ne présentera que des options de bios héritées pour l'installation.<br>

## Démarrage à partir d'un DVD
Le démarrage à partir d'un DVD est obsolète, mais les ISO d'OpenMandriva 6.0 démarrent à partir d'un DVD en utilisant le démarrage Hérité ou UEFI. Si vous rencontrez des difficultés, il existe 2 solutions [ici] (https://forum.openmandriva.org/t/4377) qui devraient vous permettre de démarrer à partir d'un DVD. Lors des tests, le démarrage d'OpenMandriva 6.0 à partir d'un DVD a pris 5-6 minutes. Cela peut prendre plus de temps sur certains matériels. L'utilisation d'un DVD à cette fin est beaucoup plus lente que l'utilisation d'une clé USB.
<br>

## À propos des dépôts
Nous avons [om-repo-picker](/policies/repositories-tldr) alias Software Repository Selector pour sélectionner des dépôts supplémentaires pour plus de disponibilité de paquets.
**Ne mélangez pas les dépôts de différentes versions/canaux de mise à jour**. Cela signifie, par exemple, qu'il ne faut pas utiliser les dépôts Cooker sur un système Rock. Si vous utilisez Rock, n'utilisez que les dépôts Rock. Ceci est expliqué plus en détail dans [Plan de publication et dépôts d'OpenMandriva](/policies/release-plan-and-repositories). Si vous mélangez différents dépôts de canaux de publication/mise à jour et que vous cassez votre ordinateur, la solution est de faire une nouvelle installation. Après cette nouvelle installation, ne recommencez pas.
<br>

## Comment installer et supprimer des paquets
Bien que les outils graphiques (Discover, dnfdragora, etc.) soient utiles pour trouver les logiciels supplémentaires disponibles, nous recommandons aux utilisateurs d'installer et de supprimer les paquets à partir de la ligne de commande :

`sudo dnf --refresh install <package_name>`

Pour supprimer un paquet :

`sudo dnf remove <package_name>`

On peut installer ou supprimer une séquence de paquets. Exemple :

`sudo dnf --refresh install <package_name_1> <package_name_2> <package_name_3> <package_name_4>`

En savoir plus sur la gestion des paquets avec dnf [ici](https://dnf.readthedocs.io/en/latest/command_ref.html).
<br>

## Procédure de mise à jour recommandée

C'est très facile, il suffit de copier et de coller cette chaîne de commande :

`sudo dnf clean all ; dnf clean all ; sudo dnf distro-sync --allowerasing --refresh`

Appuyez ensuite sur la touche Entrée et, lorsque vous y êtes invité, entrez votre mot de passe root (superutilisateur).
Nous le recommandons car nous voyons beaucoup de rapports de problèmes qui commencent par « *J'ai mis à jour mon système avec Discover updater* » ou « *J'ai mis à jour mon système avec dnfdragora* ».
<br>


## Le serveur de son par défaut a été remplacé par Pipewire
[*Pipewire*](https://pipewire.org/) est devenu notre serveur de son par défaut dans la version actuelle du système avec WirePlumber, remplaçant ainsi PulseAudio.
Cependant, PulseAudio est toujours dans notre dépôt et vous pouvez y revenir à tout moment. Pour ce faire, utilisez cette chaîne de commande :

`sudo dnf rm pipewire-pulse ; sudo dnf in pulseaudio-server`

<br>

## Noyau compilé par Clang
Le noyau standard d'OpenMandriva 6.0 est compilé par clang.
Des versions de kernel-desktop-gcc et de kernel-server-gcc sont disponibles dans les rares cas où elles sont nécessaires.
<br>

## Matériel graphique Nvidia
Ce point est abordé dans la page Errata d'OpenMandriva 6.0.
<br>

## Que faire en cas de problème ?
Si vous rencontrez des problèmes, veuillez les signaler dans le [forum d'assistance en anglais](https://forum.openmandriva.org/c/support/17) avec un titre descriptif et suffisamment de description et d'informations pour que quelqu'un puisse vous aider. Ou pour des résultats plus rapides, contactez-nous via [OpenMandriva Chat](/team/chat) . Si votre problème est un problème technique grave, veuillez [déposer un rapport de bogue](https://github.com/OpenMandrivaAssociation/distribution/issues).
<br>

## Nouveautés
Voir [Nouveauté OMLx 6.0](/distribution/releases/omlx60/new)
<br>

## Errata
Voir [OMLx 6.0 Errata](/distribution/releases/omlx60/errata)
<br>

## Aider le projet
![om-donate-32px.png](/assets/om-donate-32px.png){.align-left}Les équipes de développement d'OpenMandriva (Cooker & QA) sont toujours à la recherche de nouveaux contributeurs pour aider à la création et à la maintenance des paquets et pour aider à la correction des bogues et aux tests. Vous êtes les bienvenus pour nous rejoindre et nous aider dans ce travail qui est non seulement gratifiant mais aussi très amusant ! Si vous pensez que vos talents ne se situent pas dans le domaine du logiciel, alors le groupe OpenMandriva Workshop, qui est composé des équipes de graphisme, de documentation, de traduction et de communication, est toujours ouvert à la soumission de graphismes et de traductions. Les nouveaux contributeurs qui souhaitent participer à ces tâches très variées sont invités à consulter le wiki pour plus de détails et pour savoir comment s'inscrire ! Vous pouvez également utiliser notre [forum](https://forum.openmandriva.org).
<br>

## Faire un don au projet
![om-donate-32px.png](/assets/om-donate-32px.png){.align-left}Il faut également du temps et de l'argent pour maintenir nos serveurs en état de marche. Si vous le pouvez, merci de faire un [don](https://www.openmandriva.org/Donate) pour maintenir la flamme allumée !
<br>

![header-tr-60.svg](/assets/header-tr-60.svg){.align-abstopright}
