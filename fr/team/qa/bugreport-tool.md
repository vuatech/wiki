---
title: Outil de rapport de bogues pour OpenMandriva Lx
description: 
published: true
date: 2025-04-07T23:57:30.827Z
tags: documentation, user-guide, tools
editor: markdown
dateCreated: 2021-03-08T17:17:16.207Z
---

# Outil de rapport de bogues pour OpenMandriva Lx
Cet outil simple s'appelle om-bug-report.

## Les raccourcis
### Ouvrez OM Bienvenue et naviguez jusqu'à OM Caractéristiques > *Outil de rapport de bogues*

![om43-bugreportwelc.jpg](/images/om43-bugreportwelc.jpg)


## Informations collectées
L'outil collectera des informations utiles à partir :

- divers fichiers de configuration (dans /etc/*)
- diverses entrées /proc (qui fournissent des informations sur la configuration du noyau)
- configuration de grub (le programme de démarrage)
- Sortie lspcidrake (pour la liste des périphériques PCI)
- Sortie lsusb (pour la liste des périphériques USB)
- Sortie dmidecode (pour obtenir des informations sur le matériel à partir du BIOS)
- systemctl -failed (pour signaler les systèmes ou services dont le démarrage a échoué)
- journalctl -b (pour afficher le journal du démarrage en cours)
- rpm -qa (pour la liste des paquets installés)
- gcc version (pour la version du compilateur)

![om43-bugreportpsw.jpg](/images/om43-bugreportpsw.jpg)

![om43-bugreportpopup.jpg](/images/om43-bugreportpopup.jpg)

Il créera ensuite le fichier omdv-bug-report dans votre répertoire /home.

![om43-bugreportfile.jpg](/images/om43-bugreportfile.jpg)

> **Ce fichier doit être joint à tout rapport de bogue**.
{.is-info}

Il permettra d'accélérer le travail des chasseurs de bogues et de simplifier le travail des rapporteurs de bogues en fournissant rapidement des informations détaillées.

\- 


