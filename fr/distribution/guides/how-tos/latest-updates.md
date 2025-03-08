---
title: Comment obtenir la liste des dernières mises à jour
description: 
published: true
date: 2021-09-26T21:33:27.191Z
tags: documentation, tutoriel, guide d'utilisateur
editor: markdown
dateCreated: 2020-03-09T19:41:11.057Z
---

# Comment obtenir la liste des dernières mises à jour
Il arrive parfois que des mises à jour provoquent des dysfonctionnements et, dans ce cas, il peut être utile d'avoir à portée de main une liste des dernières mises à jour lorsque l'on recherche la source du problème.

Commençons par une liste complète, à partir de laquelle nous pourrons obtenir des informations utiles.

La commande principale est

```
rpm -qa --last
```

qui imprime ce type de liste :
.

    korganizer-17.12.2-1-omv2015.0.x86_64         Thu 15 Mar 2018 05:27:48 PM CET
    incidenceeditor-17.12.2-1-omv2015.0.x86_64    Thu 15 Mar 2018 05:27:48 PM CET
    lib64vdpau-drivers-17.3.6-1-omv2015.0.x86_64  Thu 15 Mar 2018 05:27:47 PM CET
    lib64korganizer_core5-17.12.2-1-omv2015.0.x86_64 Thu 15 Mar 2018 05:27:47 PM CET
    spectacle-17.12.2-1-omv2015.0.x86_64          Thu 15 Mar 2018 05:27:45 PM CET
    locales-en-2.27-9-omv2015.0.x86_64            Thu 15 Mar 2018 05:27:45 PM CET
    kdf-17.12.2-1-omv2015.0.x86_64                Thu 15 Mar 2018 05:27:44 PM CET
    task-plasma-5.10.5-4-omv2015.0.x86_64         Thu 15 Mar 2018 05:27:43 PM CET
    okular-tiff-17.12.2-1-omv2015.0.x86_64        Thu 15 Mar 2018 05:27:43 PM CET


Remarque : la liste peut être très longue et certaines lignes peuvent ne pas être incluses.
Pour être sûr de les voir toutes, pour la lire plus facilement ou pour la communiquer en pièce jointe, il est utile de convertir la sortie de la console en un document texte.

_Exemple_:
```
rpm -qa --last > rpmlast.txt
```
Un document `rpmlast.txt` sera créé dans votre répertoire /home.

Vous pourriez vouloir spécifier un nom de fichier différent à chaque fois que vous exécutez la commande ci-dessus afin d'obtenir un nouveau fichier et de ne pas écraser le précédent.

_Exemple_:
```
rpm -qa --last > rpmlast_20180315.txt
```

Le document peut également être enregistré au format « .csv » (Comma Separated Value), pour être facilement importé dans un tableur.
_par exemple Calc_ :

```
rpm -qa --last> rpmlast_20180315.csv
```

La liste peut contenir de nombreuses lignes, mais vous pouvez la réduire en indiquant la date.

_Exemple_:
```
rpm -qa --last | grep Mar
``` 
fournit les mises à jour effectuées en mars. Pour savoir comment raccourcir le mois, il suffit de consulter le document créé à l'aide de la commande principale illustrée ci-dessus.

Vous pouvez également limiter votre recherche à un jour spécifique :

_Exemple_:
```
rpm -qa --last | grep Thu\ 15\ Mar
```

.