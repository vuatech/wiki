---
title: OpenMandriva Lx 5.0 Errata
description: 
published: true
date: 2025-02-12T09:23:40.726Z
tags: 5.0
editor: markdown
dateCreated: 2022-12-26T17:59:33.144Z
---

# OpenMandriva Lx 5.0 Errata - Problèmes connus

> Comme pour toute version, il reste des problèmes et des bogues qui peuvent ne pas avoir été résolus. Cette page présente ceux qui peuvent causer des problèmes et, dans la mesure du possible, explique comment ils peuvent être résolus.
{.is-info}

**Veuillez également lire [5.0/Notes de version](/distribution/releases/omlx50/notes)**.
<br />

## Problèmes connus et solutions
<br />

### Cartes graphiques NVIDIA
Cette version inclut le pilote nouveau, issu du reverse engineering, qui assure une prise en charge modérément bonne de la plupart des cartes NVIDIA.
Pour certains usages sur deux écrans, il est en fait meilleur que le pilote binaire de NVIDIA car il prend en charge la rotation de l'écran sur un second moniteur, ce qui est utile pour les moniteurs à écran rotatif.
Les utilisateurs peuvent utiliser les pilotes provenant du site web de nvidia, mais ils ne sont pas pris en charge par OpenMandriva pour diverses raisons.
L'installation et la maintenance de tout pilote Nvidia propriétaire relèvent de l'option et de la responsabilité exclusives de l'utilisateur. 
Il existe des pilotes nvidia supportés par la communauté et disponibles dans les dépôts non-libres.
<br />

### Disques SSD NVME
Il existe un problème bien connu avec certains disques SSD NVME (en particulier les plus récents) et les périphériques PCIE où le disque SSD peut ne pas être reconnu.
Le problème est connu et fait l'objet de travaux de la part des développeurs d'OpenMandriva et des développeurs en amont.

![header-tr-50.svg](/assets/header-tr-50.svg){.align-abstopright}
