---
title: Comment mettre à jour le canal
description: 
published: true
date: 2025-03-10T18:03:06.852Z
tags: documentation, howto, user-guide, advanced
editor: markdown
dateCreated: 2020-04-28T08:42:49.215Z
---

# Comment mettre à jour le canal
## Comment passer de Rock à ROME (continue)

Aux utilisateurs qui découvrent OpenMandriva Lx, nous suggérons de commencer par la version stable Rock pour apprendre comment fonctionne le système, puis, si vous le souhaitez, de migrer vers ROME, l'édition continue.

Si vous êtes un utilisateur *ROME*, vous devez être capable d'utiliser la ligne de commande et connaître les bases du gestionnaire de paquets [dnf](/en/distribution/guides/software-management/DNF).
De plus, il est indispensable que l'utilisateur lise et comprenne [Plan de publication et dépôts d'OpenMandriva](/en/policies/release-plan-and-repositories).

Pour migrer vers ROME :

- Ouvrir sélecteur de dépôt de logiciels (`om-repo-picker`) 
Menu d'application > Sélecteur de dépôt de logiciels

![omlx43.doc.repopicker-01.jpg](/images/omlx43.doc.repopicker-01.jpg)

ou sélectionnez OpenMandriva repo-picker depuis OM Bienvenue

![omlx43.doc.repopicker-02.jpg](/images/omlx43.doc.repopicker-02.jpg)


- Allez à la toute première section « Mise à jour du canal ».

![om4.2-repopicker-03.jpg](/images/om4.2-repopicker-03.jpg)

- Sélectionnez « Rolling » dans le menu déroulant

![om4.2-repopicker-04.jpg](/images/om4.2-repopicker-04.jpg)

confirmez en cliquant sur OK et, lorsque vous y êtes invité, entrez votre mot de passe root. Cela prendra un certain temps et la fenêtre du programme peut devenir momentanément invisible, soyez donc patient.

Par cette action, vous avez changé les dépôts de Rock à Rolling et vous voulez donc effectuer une mise à jour du système (`distro-sync`).

- Pour mettre à jour votre système, ouvrez Konsole et exécutez les commandes suivantes :
```
$ sudo dnf clean all ; dnf clean all ; dnf repolist
$ sudo dnf --allowerasing distro-sync
```

\-
