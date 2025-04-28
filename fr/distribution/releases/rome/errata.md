---
title: OpenMandriva ROME Errata
description: ROME Errata
published: true
date: 2025-03-19T09:02:05.240Z
tags: rome
editor: markdown
dateCreated: 2023-02-28T15:18:26.632Z
---

# OpenMandriva ROME Errata - Problèmes connus

> Comme pour toute version, il reste des problèmes et des bogues qui peuvent ne pas avoir été résolus. Cette page présente ceux qui peuvent causer des problèmes et, dans la mesure du possible, explique comment ils peuvent être résolus.
{.is-info}

**Veuillez également lire [Notes ROME](/distribution/releases/rome/notes)**.
<br>

## Problèmes connus et solutions
<br>

### Steam
Le lanceur de jeu/magasin steam est disponible dans les dépôts `non-free` [*(1)*](https://wiki.openmandriva.org/en/policies/repositories-tldr#non-free) d'OpenMandriva - mais il est connu pour planter lorsqu'il est lancé pour la première fois, se plaignant de l'absence de réponse de `steamwebhelper`.

Comme Steam n'est pas Open Source, nous ne pouvons pas corriger ce problème - mais nous espérons qu'il y aura bientôt une version corrigée de Steam. En attendant, il y a une solution : tuer le processus `steamwebhelper` (si vous ne savez pas comment faire, redémarrez simplement) et redémarrer Steam.

Le deuxième lancement et tous les suivants fonctionneront.
<br>

### Cartes graphiques NVIDIA
Les membres de la communauté ont mis à disposition des pilotes propriétaires Nvidia. Le pilote `nvidia` contient le dernier pilote de production.
Veuillez également lire [Prise en charge de la version du paquet de pilotes NVIDIA](https://forum.openmandriva.org/t/5217)

Vous pouvez installer le pilote à partir du module de bienvenue d'OpenMandriva.
Gardez à l'esprit que les personnes qui mettent ces paquets à disposition le font bénévolement, en y consacrant leur temps et leurs connaissances. Il peut y avoir un délai entre la sortie d'un nouveau noyau et la sortie des paquets nvidia correspondants. 

> Ces paquets sont spécifiques au noyau. Pour l'instant, ils ne s'installeront pas si une version de noyau plus récente que celle pour laquelle ce logiciel est conçu est installée sur le système.
Plus d'informations à ce sujet [ici](https://forum.openmandriva.org/t/about-nvidia-proprietary-driver-software/4770) et [ici](https://forum.openmandriva.org/t/installing-nvidia-proprietary-drivers-in-rome/4742).
{.is-warning}

<br>

#### Problèmes connus (tous les paquets nvidia) :
1. Le code est une source fermée. Nous ne pouvons pas corriger ce qui ne fonctionne pas dans le code. Les équipes de Nvidia doivent s'en charger.

2. Le démarrage de Plymouth peut ne pas fonctionner,

3. Les terminaux virtuels peuvent ne pas fonctionner,

4. Kscreenlocker peut ne pas fonctionner,

5. Si vous utilisez `kernel-rc-desktop`, vous devrez installer `nvidia-kmod-rc-desktop`. Ou `kernel-rc-server` puis `nvidia-kmod-rc-server`.

Si vous avez un problème avec les performances graphiques des pilotes propriétaires nvidia, OpenMandriva ne peut rien y faire. Les personnes à contacter sont sur le [forum linux des développeurs Nvidia](https://forums.developer.nvidia.com/c/gpu-graphics/linux/148). OpenMandriva ne peut s'occuper que des questions liées à l'emballage de ce logiciel tiers 3rd party software et à son installation ou sa non-installation.
<br>

6. Probablement lié aux cartes graphiques nvidia :
> Il se peut que vous deviez déconnecter ou débrancher les moniteurs secondaires pour pouvoir accéder à l'écran de connexion.
{.is-warning}

<br>

#### Module de noyau ouvert Nvidia
Si votre carte est suffisamment récente (lien de la liste de compatibilité dans le sujet pertinent du forum), vous pouvez tester le [pilote ouvert](https://forum.openmandriva.org/t/6038):

Veuillez [activer le dépôt non-libre](/policies/repositories-tldr#non-free) et exécutez la commande :
`sudo dnf install nvidia nvidia-kmod-open-desktop --refresh`

Si vous avez déjà installé le pilote propriétaire du module de [OM Bienvenue](/distribution/software/om-welcome), vous pourrez peut-être exécuter la même commande sans le nom du paquet nvidia. Dans tous les cas, vous devrez redémarrer après l'installation.
<br>

### Comment installer X11 sur le système Plasma6 Wayland
#### Pour les utilisateurs de Plasma 6 :

`sudo dnf in task-plasma6-x11 --refresh`

Cela permet à l'utilisateur de comparer X11 à Wayland. Il est connu qu'il y a des problèmes avec Wayland dans Plasma 6. C'est un moyen utile de déterminer si le problème est en fait lié à Wayland ou non. Essentiel pour les demandes de support dans le forum OM et les rapports de bogues. Également utile si, pour une raison quelconque, Wayland ne fonctionne pas pour l'utilisateur.

### Comment installer Wayland sur un système Plasma 6 X11
#### Pour les utilisateurs de Plasma 6 :

`sudo dnf in task-plasma6-wayland --refresh`

Cela permet aux utilisateurs de comparer Wayland à X11.
<br>

### Disques SSD NVME
Les disques SSD NVME sont normalement reconnus par le Live ISO de ROME. Si, pour une raison quelconque, ils ne le sont pas, nous avons quelques solutions de contournement sous 'Troubleshooting' dans le menu Grub2 de l'ISO qui peuvent fonctionner. Il s'agit de (PCIE ASPM=OFF) et (NVME APST=OFF). Nous espérons que cela fonctionnera avec le matériel de la plupart des utilisateurs.
Ce problème est bien sûr très spécifique au matériel.

Lorsqu'il se produit, ce problème est causé par un micrologiciel défectueux dans les périphériques NVMe. Si le fabricant de l'appareil fournit une mise à jour du micrologiciel, vous pouvez vérifier si cela résout le problème sans avoir à désactiver l'ASPM.

L'ASPM (Active State Power Management) peut réduire la consommation d'énergie des périphériques NVMe. Il n'est donc pas recommandé de le désactiver, sauf en cas de nécessité.

Sur le système installé, l'utilisateur peut souhaiter ajouter cette solution à `/etc/default/grub` et exécuter update-grub2 pour rendre la solution globale. Vous devez utiliser la solution que vous avez trouvée sur le Live ISO.

Si (PCIE ASPM=OFF) a fonctionné pour vous, ajoutez :
`pcie=aspm=off`
aux lignes :
`GRUB_DECLINE_LINUX_DEFAULT`
`GRUB_DECLINE_LINUX_RECOVERY`
dans
`/etc/default/grub`
puis exécutez :
`$ sudo update-grub2`

Si (NVME APST=OFF) a fonctionné, ajouter à la place :
`nvme_core.default_ps_max_latency_us=0`

Comme toujours, les utilisateurs sont encouragés à poser des questions sur tout ce qu'ils ne comprennent pas sur notre [forum](https://forum.openmandriva.org/).
<br>

### Installation à partir de Ventoy
***Ce problème devrait maintenant être résolu***

Solution de contournement précédente si nécessaire :

Copiez votre fichier .iso OMLx dans la partition Ventoy sur la clé USB Ventoy. Démarrez-le.

1. Ouvrez Konsole (terminal) et `cd /run/initramfs/omdv/LiveOS`
2. tapez `ls` et vérifiez que `squashfs.img` est présent
3. Laissez Konsole (terminal) ouvert dans ce répertoire.
4. Ouvrez le programme d'installation Calamares OMLx et installez votre nouveau système.

Il semble que tant que ce répertoire est ouvert et que `ls` montre que `squashfs.img` est présent, l'utilisateur sera en mesure d'installer le système OMLx qu'il souhaite à partir de la clé Ventoy.

Si cela ne fonctionne pas, peut-être que ceci fonctionnera :

1. Ouvrez Konsole (terminal) cd vers « `/run/initramfs/omdv/LiveOS` »,
puis
`cp squashfs.img /live`
Vous devez faire cette étape immédiatement après avoir démarré l'ISO 'Live' ou le dossier `/run/initramfs/omdv/LiveOS` disparaîtra ou ne sera pas reconnu. Après avoir fait ce `cp`, ce dossier disparaîtra donc ensuite :
2. `$ sudo mkdir /run/initramfs/omdv/LiveOS`
3. `$ sudo cp /live/squashfs.img /run/initramfs/omdv/LiveOS`
4. Pour vérifier :
```
 $ ls -la /run/initramfs/omdv/LiveOS
total 2867796
drwxr-xr-x 2 root root         60 Oct 19 20:30 .
drwxr-xr-x 3 root root         60 Oct 19 20:29 ..
-r--r--r-- 1 root root 2936623104 Oct 19 20:30 squashfs.img
```
5. Install OMLx

<br>

### GEOIP
Le réglage automatique GEOIP de l'installateur peut ne pas définir correctement votre fuseau horaire (il devine votre emplacement sur la base de votre adresse IP).
S'il détecte votre fuseau horaire de manière incorrecte, il vous suffit de sélectionner manuellement le fuseau horaire correct.
<br>

### Ajouter/supprimer des favoris dans le lanceur d'applications
***Dans Plasma 6*** cela a été corrigé.

***Dans Plasma 5*** il existe toujours un bogue en amont concernant l'ajout et la suppression de favoris dans le lanceur d'applications
L'utilisateur a le choix entre 2 solutions de contournement :
•Ajoutez ou supprimez les applications que vous souhaitez voir figurer dans la colonne Favoris du Lanceur d'applications. Cliquez ensuite avec le bouton droit de la souris sur l'icône du lanceur d'applications et sélectionnez « Afficher les alternatives » pour passer à l'un des autres lanceurs. Cliquez ensuite à nouveau avec le bouton droit de la souris sur le lanceur d'applications et revenez en arrière.
•Ajoutez ou supprimez les applications que vous souhaitez dans la colonne Favoris du Lanceur d'applications. Ensuite, déconnectez-vous et connectez-vous.
<br>

### Comment configurer l'imprimante
[*Lire aussi : Imprimante*](/en/distribution/guides/how-tos/printer)
Mettez votre imprimante sous tension et vérifiez si elle est configurée automatiquement. Vérifiez si le bon pilote a été installé. Si l'imprimante a été configurée automatiquement et que vous avez le bon pilote, c'est parfait, vous êtes prêt.
Si ce n'est pas le cas, mettez votre imprimante hors tension. Ouvrez la fenêtre Paramètres système>Matériel>Imprimantes ou à partir d'un terminal (Konsole) :

`kcmshell6 kcm_printer_manager`

(si vous utilisez Plasma 5, utilisez `kcmshell5` au lieu de `kcmshell6`) et supprimez votre imprimante dans le dialogue de l'interface utilisateur.
Si le pilote correct n'a pas été installé par défaut, nous devrons ajouter un logiciel.
L'étape suivante consiste à déterminer le logiciel (le cas échéant) à ajouter pour votre imprimante.
Dans OpenMandriva Lx, il s'agira probablement d'un paquetage 'task-printing' spécifique à votre marque d'imprimante. Les paquets sont les suivants :

•task-printing-canon
•task-printing-epson
•task-printing-hp
•task-printing-lexmark
•task-printing-okidata
•brlaser (pour les imprimantes Brother)
•task-printing-misc

Installez le paquet qui correspond à votre marque ou le paquet divers s'il n'y en a pas. Exemple avec okidata :

`sudo dnf install task-printing-okidata`

Rallumez l'imprimante et elle devrait se configurer automatiquement (il faut parfois redémarrer l'imprimante pour que la configuration automatique fonctionne). Si ce n'est pas le cas, vous pouvez la configurer à l'aide de Paramètres système>Matériel>Imprimantes ou à partir d'un terminal (Konsole) :

`kcmshell6 kcm_printer_manager`.

**Une autre méthode pour configurer une imprimante dans ROME consiste à utiliser CUPS (https://localhost:631/ comme url dans le navigateur)**. *Pour certains matériels, cette méthode peut s'avérer plus efficace.*

Si ce n'est pas le cas, demandez de l'aide [ici](https://forum.openmandriva.org/c/en/support).

**Remarque :** Si vous avez des problèmes pour configurer une imprimante connectée en USB, il peut être utile de supprimer les paquets `usbmuxd` et `ipp-usb`. Supprimer `ipp-usb` signifie que vous ne pourrez pas utiliser le pilote « sans pilote ».
<br>

### Découvrir de nouveaux logiciels
Si vous souhaitez explorer d'autres dépôts, vous devrez les activer au moyen du [Sélecteur de dépôt logiciel](/policies/repositories-tldr) et rafraîchir le cache. Pour rafraîchir le cache, vous pouvez utiliser l'option `--refresh` comme ceci :

`sudo dnf --refresh install foo_package`

Ou vous pouvez utiliser `dnf clean all` comme :

`sudo dnf clean all ; sudo dnf install foo_package`
<br>

### Mesa et VirtualBox
***Ce problème devrait maintenant être résolu***

VirtualBox exécutant Plasma x11 ISO ne gère pas très bien mesa 24.2.x ([upstream bugtracker report](https://gitlab.freedesktop.org/mesa/mesa/-/issues/11818)).
Il se peut que vous constatiez des imperfections telles que des ombres manquantes ou d'autres artefacts.
Avec du matériel réel ou qemu (ou tout autre logiciel de virtualisation qui émule un véritable GPU), les graphiques s'affichent correctement.
Avec l'ISO Plasma wayland, le problème n'apparaît pas.
Solution possible pour les utilisateurs de VirtualBox : passer à la version 24.1.7 de mesa.
<br>

### Contrôleur graphique dans VirtualBox 7.0.x
Les images d'installation OMLX les plus récentes peuvent nécessiter que le contrôleur VMSVGA soit configuré pour démarrer avec succès dans VirtualBox 7.0.x.
<br>

### Son dans VirtualBox 7.0.x
Certains utilisateurs signalent des problèmes de son haché ou saccadé dans OM VirtualBox 7.0.x.
Ce problème semble être lié au matériel de l'utilisateur. Les développeurs sont conscients de ce problème et recherchent activement une solution. Les utilisateurs doivent garder à l'esprit que le son dans VirtualBox est une émulation et que le processus est sujet à des problèmes périodiques. *Ainsi, l'utilisation de VirtualBox pour le multimédia est susceptible d'avoir des problèmes périodiques.*
<br>

### Multiboot
Dans le « monde réel », le multiboot fonctionne bien la plupart du temps, mais lorsqu'il y a des problèmes, la solution est parfois une solution de contournement plutôt qu'un correctif. Ce ne sont que des réalités du multiboot.
Il n'est pas non plus possible pour OpenMandriva QA de tester notre chargeur de démarrage avec tous les types de systèmes de fichiers sur toutes les distributions Linux, ni même sur le « Top 10 » des distributions Linux. Le fait est que, que ce soit pour le multi-boot avec Windows ou d'autres distros Linux, nous nous appuyons exclusivement sur les rapports des utilisateurs pour savoir ce qui fonctionne et ce qui ne fonctionne pas en matière de multi-boot.
Un problème connu rencontré avec le programme d'amorçage OMLx est que OpenMandriva grub2 ne crée pas d'entrées d'amorçage pour les systèmes openSUSE qui utilisent le système de fichiers btrfs. OMLx grub2 fonctionne avec les systèmes openSUSE qui utilisent le système de fichiers ext4.
Ceci est dû au fait qu'openSUSE utilise une syntaxe personnalisée pour ses correctifs btrfs pour les paquets openSUSE os-prober et grub2 qui ne sont pas compatibles avec le code OMLx. On ne sait pas encore si le chargeur de démarrage OMLx fonctionne ou non avec openSUSE avec d'autres types de systèmes de fichiers tels que XFS ou F2FS.
La solution consiste pour les utilisateurs à changer de chargeur de démarrage dans les paramètres du micrologiciel UEFI ou du BIOS pour utiliser le chargeur de démarrage openSUSE.

Au fur et à mesure que les utilisateurs nous signalent des problèmes liés au multiboot, nous corrigeons ce qui peut l'être. Les problèmes que nous ne pouvons pas résoudre seront signalés dans les Errata de nos versions OMLx.
<br>

### Serveur de sons Pipewire
Certains utilisateurs peuvent rencontrer des problèmes avec le nouveau serveur de son Pipewire. Si c'est le cas, l'utilisateur peut passer à l'ancien serveur de son pulseaudio. Pour ce faire, ouvrez Konsole et exécutez la commande copier-coller suivante :

`$ sudo dnf remove pipewire-pulse ; sudo dnf install pulseaudio-server`
<br>

### Zypper
Le paquet `zypper-needs-restarting` est en conflit avec `dnf-utils` s'il est installé.
Comme solution de contournement, supprimez `dnf-utils`.
<br>

### Bluetooth
Pour les périphériques Bluetooth, l'utilisateur peut avoir besoin d'activer systemd bluetooth.service. Ouvrir Konsole
et exécutez :

`$ sudo systemctl start bluetooth ; sudo systemctl enable bluetooth`
<br>

### SystemSettings
***Ce problème devrait maintenant être résolu***
Certains modules de SystemSettings peuvent ne pas s'afficher correctement lors du premier lancement.
Ils s'afficheront lors de la prochaine connexion.
<br>

## Que faire en cas de problème ?
Si vous rencontrez des problèmes, veuillez les signaler dans le [forum d'assistance en anglais](https://forum.openmandriva.org/c/en/support)avec un titre descriptif et suffisamment de description et d'informations pour que quelqu'un puisse vous aider. Ou pour des résultats plus rapides, contactez-nous via [OpenMandriva Chat](https://wiki.openmandriva.org/en/team/chat) .  Si votre problème est un problème technique grave, veuillez [déposer un rapport de bogue](https://github.com/OpenMandrivaAssociation/distribution/issues).
<br>

## Aider le projet
![om-donate-32px.png](/assets/om-donate-32px.png){.align-left}Les équipes de développement d'OpenMandriva (Cooker & QA) sont toujours à la recherche de nouveaux contributeurs pour aider à la création et à la maintenance des paquets et pour aider à la correction des bogues et aux tests. Vous êtes les bienvenus pour nous rejoindre et nous aider dans ce travail qui est non seulement gratifiant mais aussi très amusant !
Si vous estimez que vos talents ne se situent pas dans le domaine du logiciel, le groupe OpenMandriva Workshop, composé des équipes chargées des illustrations, de la documentation, de la traduction et de la communication, est toujours ouvert à la soumission d'illustrations et de traductions.
Les nouveaux contributeurs qui souhaitent participer à ces tâches de grande envergure sont invités à consulter le wiki pour plus de détails et pour savoir comment s'inscrire ! Vous pouvez également utiliser notre [forum](https://forum.openmandriva.org).
Le maintien de nos serveurs en état de marche coûte également du temps et de l'argent.
Si vous le pouvez, faites un [don](https://www.openmandriva.org/Donate) pour maintenir la flamme allumée !
<br>

![header-tr-rome.svg](/assets/header-tr-rome.svg){.align-abstopright}