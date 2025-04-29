---
title: AQ/Pour commencer
description: 
published: true
date: 2025-02-11T09:38:33.447Z
tags: qa, documentation
editor: markdown
dateCreated: 2020-03-02T15:35:06.431Z
---

# Débuter avec l'AQ
Nous sommes heureux que vous vous intéressiez à l'assurance qualité.
Nous avons compilé ce document pour vous aider à commencer à nous aider à tester OpenMandriva Lx.

La plupart du temps, vous devrez utiliser la ligne de commande pour tester. Assurez-vous d'avoir un compte sur [ABF](https://abf.openmandriva.org/) et [Github](https://github.com/OpenMandrivaAssociation).

La communication quotidienne de l'équipe AQ a lieu sur Matrix Chat `#openmandriva-cooker:matrix.org` mais n'oubliez pas que c'est aussi là que les développeurs travaillent, alors faites attention à votre nétiquette IRC. 
Actuellement, le groupe de contributeurs d'OpenMandriva est suffisamment petit pour que les développeurs et l'assurance qualité travaillent ensemble sur les salons Matrix. Il existe également un [Forum AQ](https://forum.openmandriva.org/c/en/qa).

Les membres de l'équipe d'AQ sont encouragés à participer activement aux réunions hebdomadaires (dans la mesure du possible) du CT.
</br>

### Configuration de votre système OpenMandriva Lx
Comme vous travaillerez probablement avec des logiciels non testés (du moins avec notre système d'exploitation), nous vous conseillons vivement d'utiliser une machine dédiée ou virtuelle pour les tests. Pour le travail d'assurance qualité sur le matériel (recommandé si possible), il est conseillé d'installer Rolling sur une partition séparée afin de disposer d'un système « stable » sur une autre partition au cas où quelque chose se casserait pendant les tests.

Les logiciels en préversion proviennent des dépôts de test. Les paquets du dépôt principal sont prioritaires sur ceux des autres dépôts. Les paquets dans les dépôts Unsupported et Non-Free sont sous la responsabilité du mainteneur du paquet et non des développeurs d'OpenMandriva.

Les membres de l'équipe AQ doivent avoir une compréhension approfondie du [Plan de publication et dépôts](/policies/release-plan-and-repositories) et des [Politiques de dépôt](/policies/repository-policies). Il y en aura d'autres au fur et à mesure que nous documenterons mieux Openmandriva Lx, mais nous aimons garder la documentation aussi simple et légère que possible.

Le flux de travail pour les paquets est le suivant : Cooker > Rolling > Dépôt stable. Les développeurs/mainteneurs de paquets sont responsables de l'initiation des paquets dans Cooker et de leur déplacement vers les dépôts rolling/testing. L'assurance qualité prend ensuite le relais. Ainsi, tous les membres de l'équipe d'assurance qualité sont encouragés à maintenir un système Rolling où ils peuvent tester les paquets.

Vous pouvez ajouter les dépôts de test avec l'interface graphique d'OpenMandriva [Sélécteur de dépôts logiciels](/policies/repositories-tldr), ou à partir de la ligne de commande.

Pour le dépôt principal uniquement :

Système Rock :
`sudo dnf config-manager --enable rock-testing-$ARCH`

Système continu :
`sudo dnf config-manager --enable rolling-testing-$ARCH`

Remplacez `$ARCH` par votre architecture.

Pour tous les dépôts de test :

Système Rock :
`sudo dnf config-manager --enable rock-testing-$ARCH rock-testing-$ARCH-unsupported rock-testing-$ARCH-restricted rock-testing-$ARCH-non-free`

Système continu :
`sudo dnf config-manager --enable rolling-testing-$ARCH rolling-testing-$ARCH-unsupported rolling-testing-$ARCH-restricted rolling-testing-$ARCH-non-free`

Pour désactiver, il suffit de remplacer `--enable` par `--disable`.
</br>

### Tests de paquets avec Kahinah
Maintenant que votre système est en place, il est temps de voter pour les paquets. Fonctionnent-ils ? Y a-t-il des problèmes vraiment graves ?

Nous utilisons un système appelé [Kahinah](https://kahinah.tsn.sh/), qui utilise le vote pour déterminer quels paquets doivent être poussés vers le dépôt stable ou non.
Connectez-vous à Kahinah. Utilisez votre login Github.
Vous pouvez voir quels paquets attendent d'être testés dans la rubrique « Constructions récentes ». Donnez-lui un pouce en l'air ou un pouce en bas, et faites-nous savoir pourquoi.

La procédure actuelle veut que les paquets nécessitent 3 votes d'acceptation pour avancer, à moins qu'il n'y ait des votes de rejet. S'il y a ne serait-ce qu'un vote « Rejet », il doit être remis en question et discuté avant de déplacer les paquets. De même, les paquets qui restent bloqués dans Kahinah sans aucun vote pendant plus de 7 jours peuvent être déplacés en raison de l'inaction de l'AQ. Les discussions à ce sujet ont lieu sur le canal IRC Libera.Chat #openmandriva-cooker.
</br>

### Test des nouvelles ISO Alpha/Beta/RC
Ce point est abordé [ici](/team/qa/release-qa).
</br>

### Triage des nouveaux bogues dans l'Issue Tracker
https://github.com/OpenMandrivaAssociation/distribution/issues
Ce processus est actuellement en cours de développement. (Nous devons mettre en place un système de triage des rapports de bogues). 