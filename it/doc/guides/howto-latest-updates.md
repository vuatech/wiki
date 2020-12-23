---
title: Come ottenere un elenco degli ultimi aggiornamenti
description: 
published: true
date: 2020-12-21T23:54:03.358Z
tags: 
editor: undefined
dateCreated: 2020-04-15T09:31:23.013Z
---

# Come ottenere un elenco degli ultimi aggiornamenti

A volte gli aggiornamenti possono causare qualche tipo di malfunzionamento e in tal caso può essere utile avere a portata di mano un elenco degli ultimi aggiornamenti mentre si cerca la fonte del problema.

Cominciamo con un elenco completo, dal quale possiamo ricavare alcune informazioni utili.

Il comando principale è

```
rpm -qa --last
```

che stampa una lista di questo tipo:
```
    korganizer-17.12.2-1-omv2015.0.x86_64         Thu 15 Mar 2018 05:27:48 PM CET
    incidenceeditor-17.12.2-1-omv2015.0.x86_64    Thu 15 Mar 2018 05:27:48 PM CET
    lib64vdpau-drivers-17.3.6-1-omv2015.0.x86_64  Thu 15 Mar 2018 05:27:47 PM CET
    lib64korganizer_core5-17.12.2-1-omv2015.0.x86_64 Thu 15 Mar 2018 05:27:47 PM CET
    spectacle-17.12.2-1-omv2015.0.x86_64          Thu 15 Mar 2018 05:27:45 PM CET
    locales-en-2.27-9-omv2015.0.x86_64            Thu 15 Mar 2018 05:27:45 PM CET
    kdf-17.12.2-1-omv2015.0.x86_64                Thu 15 Mar 2018 05:27:44 PM CET
    task-plasma-5.10.5-4-omv2015.0.x86_64         Thu 15 Mar 2018 05:27:43 PM CET
    okular-tiff-17.12.2-1-omv2015.0.x86_64        Thu 15 Mar 2018 05:27:43 PM CET
```
Nota: la lista può essere molto lunga e alcune righe potrebbero non essere incluse.
Per avere la certezza di vederle tutte, per leggerle più facilmente o per fornirle come allegato, è utile convertire l'output della console in un documento di testo.

*Esempio*:

```
rpm -qa --last > rpmlast.txt
```

Un documento `rpmlast.txt` verrà creato nella tua directory /home.

È possibile specificare un nome di file diverso ogni volta che si esegue il comando di cui sopra per ottenere un nuovo file e non sovrascrivere il precedente.

*Esempio*:

```
rpm -qa --last > rpmlast_20180315.txt
```

Il documento può anche essere salvato in formato ".csv" (Comma Separated Value), per essere facilmente importato in un foglio elettronico
*per esempio Calc*:

```
rpm -qa --last> rpmlast_20180315.csv
```

La lista può contenere molte righe, ma è possibile restringere l'elenco indicando la data

*Esempio*:

```
rpm -qa --last | grep Mar
``` 

fornisce gli aggiornamenti effettuati nel mese di marzo. Per sapere come abbreviare il mese basta guardare nel documento creato con il comando principale mostrato sopra.

È anche possibile limitare la ricerca ad un giorno specifico:

*Esempio*:

```
rpm -qa --last | grep Thu\ 15\ Mar
```
\-

