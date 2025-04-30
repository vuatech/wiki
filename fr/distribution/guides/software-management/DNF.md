---
title: Utiliser dnf dans OpenMandriva Lx
description: 
published: true
date: 2025-02-15T11:00:42.718Z
tags: documentation, dnf, user-guide
editor: markdown
dateCreated: 2020-03-06T18:48:34.373Z
---

# Utiliser dnf dans OpenMandriva Lx

> Pour une documentation complète et d'autres commandes, voir [Référence des commandes DNF](https://dnf.readthedocs.io/en/latest/command_ref.html)
{.is-success}


## Quelques commandes élémentaires

- installer un paquet :
`$ sudo dnf --refresh install <package_name>`

- supprimer un paquet :
`$ sudo dnf remove <package_name>`

- rechercher un paquet dans les dépôts :
`$ sudo dnf search <package_name>`
Remarque : 'dnf search' fonctionne également avec des noms partiels.

- nettoyer les fichiers et les paquets conservés en cache et supprimer les métadonnées du dépôt :
`$ sudo dnf clean all ; dnf clean all`

- mettre à jour votre système Rock :
`$ sudo dnf --refresh upgrade `

- mettre à jour votre système rolling :
`$ sudo dnf --refresh distro-sync `

## Autres commandes dnf courantes

`autoremove`
supprime les paquets installés en tant que dépendances qui ne sont plus nécessaires aux programmes actuellement installés.
> Soyez prudent et faites attention lorsque vous utilisez `dnf autoremove`. Il est tout à fait possible que cela supprime quelque chose que vous ne voulez pas supprimer. C'est une bonne idée de garder une liste des paquets qui ont été supprimés automatiquement afin de savoir quoi réinstaller si cela se produit.
Note : Vous pouvez trouver les paquets supprimés automatiquement dans `/var/log/dnf.log`
{.is-warning}


`check-update`
vérifie les mises à jour, mais ne télécharge ni n'installe les paquets

`downgrade`
revient à la version précédente d'un paquet

`info`
fournit des informations de base sur le paquet, y compris le nom, la version, l'édition et la description.

`reinstall`
réinstalle le paquet actuellement installé

`repolist`
liste des dépôts activés

## Certaines commandes peuvent être abrégées

`dnf in=dnf install`
`dnf ri=dnf reinstall`
`dnf dg=dnf downgrade`
`dnf rm=dnf remove`
`dnf up=dnf upgrade`
`dnf dsync=dnf distro-sync`

## Quelques options courantes de dnf

`--allowerasing`
Permet d'effacer les paquets installés pour résoudre les dépendances. Cette option peut être utilisée comme alternative à la commande yum swap lorsque les paquets à supprimer ne sont pas explicitement définis. Utilisez-la avec précaution, sachez ce que vous faites ou vous risquez de casser votre système.

`-b, --best`
Essaie les meilleures versions de paquets disponibles dans les opérations. Spécifiquement lors de la mise à jour de dnf, qui par défaut ignore les mises à jour qui ne peuvent pas être installées pour des raisons de dépendance, le changement force DNF à ne prendre en compte que les derniers paquets. Lorsque vous rencontrez des paquets dont les dépendances sont rompues, DNF échoue en donnant une raison pour laquelle la dernière version ne peut pas être installée.

`--disable, --set-disabled`
Désactive les dépôts spécifiés (sauvegarde automatique). Cette option doit être utilisée avec la commande config-manager (dnf-plugins-core).

`--disablerepo=<repoid>`
Désactive des dépôts spécifiques par un identifiant ou un glob. Cette option est mutuellement exclusive avec `--repo`.

`--downloadonly`
Télécharge l'ensemble de paquets résolus sans effectuer de transaction rpm (installation/mise à jour/effacement).

`--enable, --set-enabled`
Active les dépôts spécifiés (sauvegarde automatique). L'option doit être utilisée avec la commande config-manager (dnf-plugins-core).

`--enablerepo=<repoid>`
Active des dépôts supplémentaires par un identifiant ou un glob

`--exclude=<package_name>`
Exclu certains paquets de l'opération

`--nobest`
Définir la meilleure option sur Faux, afin que les opérations ne soient pas limitées aux meilleurs candidats.

`-y, --assumeyes`
Répondre automatiquement par l'affirmative à toutes les questions

## Plus
`$ dnf --help`
et
`$ man dnf4` or `$ man dnf5` 

La liste d'aide prend environ une minute à une minute et demie à lire. La page de manuel prend environ 3-5 minutes.
Les deux sont destinés à être mis à la disposition des utilisateurs pour qu'ils puissent s'y référer lorsqu'ils utilisent leur système et ont besoin de trouver rapidement comment faire quelque chose.

Il existe également des pages wiki et des documents sur dnf : [Utiliser le gestionnaire de paquets DNF](https://docs.fedoraproject.org/en-US/quick-docs/dnf/), [Page wiki Fedora](https://fedoraproject.org/wiki/DNF?rd=Dnf), et [Référence de commande DNF](https://dnf.readthedocs.io/en/latest/command_ref.html).


