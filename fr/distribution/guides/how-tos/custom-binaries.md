---
title: Comment compiler votre propre logiciel
description: 
published: false
date: 2024-01-24T01:07:05.893Z
tags: clang
editor: markdown
dateCreated: 2024-01-24T00:23:36.493Z
---

# Clang
Une caractéristique unique d'OpenMandriva est l'utilisation de *clang* comme compilateur de base. 

> GCC est toujours disponible mais a été complètement abandonné en faveur de CLANG depuis OpenMandriva version 5.0
> Il n'est plus possible d'utiliser gcc pour compiler les modules du noyau par exemple ! {.is-warning}

## Commencer

1. Avant de compiler votre propre logiciel, assurez-vous qu'il n'existe pas déjà dans l'un de nos dépôts.
2. Vous pouvez également demander à notre équipe d'ajouter le paquet depuis le forum ou directement sur github.

## Démarrage rapide

Vous pouvez installer les outils de développement de base à partir de l'application OM Welcome :
![om5-welcome-devtools.png](/images/om5-welcome-devtools.png)

A partir du terminal, vous pouvez taper

```bash
sudo dnf install task-devel task-c-devel task-c++-devel
```

Exemple de commande make pour compiler un logiciel localement sur votre machine :

## Compilateur

Par défaut, les logiciels peuvent utiliser gcc comme base. Vous devez essayer avec clang.
Voici un exemple de commande make personnalisée

```bash
make CC=clang CXX=clang++ LD=ld.lld AR=llvm-ar NM=llvm-nm OBJCOPY=llvm-objcopy OBJSIZE=llvm-size STRIP=llvm-strip -C ...
```

## Mise en paquet

Si vous souhaitez aller plus loin, vous êtes invité à rejoindre notre groupe de travail chargé de l'empaquetage des logiciels. 