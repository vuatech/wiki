---
title: Comment créer les partitions root home et swap lors de l'installation d'OMLx ?
description: 
published: true
date: 2021-09-26T22:10:40.796Z
tags: documentation, tutoriel, guide d'utilisateur, avancé
editor: markdown
dateCreated: 2020-03-10T15:27:21.952Z
---

# Comment créer les partitions root home et swap lors de l'installation d'OMLx ?

L'installateur d'OpenMandriva est [Calamares](http://calamares.io/).
Il est facile, utilisable, beau, pragmatique, inclusif et indépendant de la distribution.
Calamares inclut une fonction de partitionnement avancée, avec un support pour les opérations de partitionnement manuelles et automatisées.

> Note : Lorsque vous lisez *Lx 4*, cela inclut toutes les versions 4.x comme 4.0, 4.1, et 4.2. Ce how-to est applicable à toutes les versions d'OMLx, y compris Cooker et Rolling, ainsi qu'à la famille Lx 4.
{.is-info}


Pour faire à peu près tout ce que vous voulez avec les partitions, vous devez sélectionner <kbd>Partitionnement manuel</kbd>

![root-home-swap-01.png](/images/root-home-swap-01.png)

Notez que si vous acceptez l'option par défaut <kbd>Effacer le disque </kbd> il créera uniquement une partition `/boot/efi` et `/`.
Par défaut, le programme d'installation ne crée plus automatiquement une partition de swap, car sur la plupart des ordinateurs modernes, le swap n'est plus utilisé.

Sélectionnez <kbd>Partitionnement Manuel</kbd>

![root-home-swap-02.png](/images/root-home-swap-02.png)

Tout d'abord, nous verrons comment configurer un système efi avec des partitions `/`, `/home` et `swap` séparées, ainsi que la partition `/boot/efi` nécessaire au démarrage de l'efi. Si vous utilisez la table de partition MBR, vous n'avez pas besoin de créer une partition `/boot/efi`.
La partition `/boot/efi` doit être étiquetée avec `boot`. (Le partitionneur l'appellera automatiquement `esp`.)

La première étape consiste à sélectionner <kbd>Nouvelle table de partition</kbd>
Si le système est démarré par efi ou uefi, il doit correspondre à une table de partitions `GPT`..
S'il s'agit d'un boot legacy, vous pouvez sélectionner soit `MBR` soit `GPT`. Si vous ne savez pas laquelle utiliser, choisissez la plus récente, `GPT`. De plus, si l'utilisateur a plusieurs disques durs ou SSD, ils doivent tous avoir le même type de table de partition, sinon il peut y avoir des problèmes. Donc tous les `GPT` ou tous les `MBR`.

![root-home-swap-03.png](/images/root-home-swap-03.png)

Ensuite, nous allons créer `/boot/efi`, `/`, `/home`, et swap dans cet ordre.
Le seul facteur critique dans l'ordre est que `/boot/efi` doit être en premier, les autres peuvent être dans n'importe quel ordre.

`/boot/efi` est typiquement une partition de 300 MB et doit être fat16 ou fat32 pour fonctionner. Dans certains autres installateurs, son système de fichiers sera appelé vfat.

Nous les créerons donc un par un.
Sélectionner <kbd>Créer</kbd>

![root-home-swap-04.png](/images/root-home-swap-04.png)

Suivez les étapes de la boîte de dialogue et vous obtiendrez quelque chose comme ceci

![root-home-swap-06.png](/images/root-home-swap-06.png)

Si vous avez ce que vous voulez, sélectionnez <kbd>Suivant</kbd> et, une fois installé, votre nouveau système disposera de partitions distinctes pour la root, home et le swap.

Notez que `/boot/efi` est en haut de la liste en première position. C'est nécessaire.

> Notez que votre partition d'échange ne sera probablement jamais utilisée. De nos jours, seule une petite minorité d'utilisateurs a réellement besoin d'une partition d'échange. Ceux qui en ont besoin savent déjà qui vous êtes et peuvent s'adapter en conséquence. En général, ce sont les très vieux ordinateurs qui n'ont pas assez de mémoire vive pour faire tourner Lx 4 qui ont besoin d'une partition d'échange. Quelle quantité de RAM est suffisante ? Idéalement, 4 Go. Nous avons des utilisateurs qui utilisent Lx 4 avec 2 Go. Les notes de mise à jour pour Lx 4.0 et 4.1 indiquent 2 Go et le programme d'installation de Calamares requiert 2 Go. La mise à niveau de la mémoire d'un ordinateur, qu'il s'agisse d'un ordinateur de bureau, d'une tour ou d'un ordinateur portable, est à la fois facile et peu coûteuse de nos jours. Si votre ordinateur manque de mémoire, pensez à le mettre à niveau.
Le swap peut également être utilisé sur des ordinateurs effectuant des calculs mathématiques ou scientifiques très poussés ou des applications graphiques très intenses. Mais ces utilisateurs sauront ce dont ils ont besoin.
{.is-info}


Voici une capture d'écran de la fenêtre de dialogue de <kbd>Création</kbd> pour votre partition `/boot/efi` sur un système `UEFI/EFI` :

![root-home-swap-05.png](/images/root-home-swap-05.png)

\-
