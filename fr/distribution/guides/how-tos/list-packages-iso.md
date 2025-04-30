---
title: Comment obtenir une liste de tous les paquets inclus dans l'ISO ?
description: 
published: true
date: 2022-04-02T15:42:47.137Z
tags: documentation, howto, user-guide
editor: markdown
dateCreated: 2020-03-09T19:56:46.846Z
---

# Comment obtenir une liste de tous les paquets inclus dans l'ISO ?


En mode Live, ouvrez la console et tapez :

```
rpm -qa|sort > pkglist-sort.txt
```
ce qui créera un document en texte brut dans le répertoire `/home` de votre utilisateur, nommé `pkglist-sort.txt`

La liste des paquets est triée de A à Z

![pkglist.jpg](/images/pkglist.jpg)

> Cette astuce simple s'applique non seulement au mode ISO/Live, mais aussi aux systèmes installés.
> Vous pouvez exécuter la commande à tout moment.
{.is-info}


Si vous souhaitez obtenir une liste de tous les paquets triés par date, tapez :

```
rpm -qa --last > pkglist-last.txt
```

