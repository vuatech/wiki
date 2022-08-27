---
title: Mirroring
description: 
published: true
date: 2021-09-26T21:37:55.684Z
tags: documentation
editor: markdown
dateCreated: 2020-05-02T21:51:00.325Z
---

# Mirroring
## Lista dei mirror attivi (Mirmon)
`http://downloads.openmandriva.org/mm/`

## Lista dei mirror per configurare i media
`http://downloads.openmandriva.org/mirrors/`

## Configurare un mirror
Per favore segui questo processo:
* Usa uno dei nostri mirror T-1

`http://mirror.yandex.ru/openmandriva/`
`http://distro.ibiblio.org/openmandriva/`

Per esempio con con questo comando:

`rsync -av rsync://mirror.yandex.ru/openmandriva/ /local/path`
`rsync -av distro.ibiblio.org::openmandriva/ /local/path/`
> Non dimenticare il file "TIME", che serve a Mirmon per funzionare correttamente.
>
> Sono necessari come minimo "300GB" di spazio libero su disco
{.is-warning}


Nota: La fonte è:
`http://abf-downloads.openmandriva.org`

Questo server serve solo ad inviare i dati necessari a Yandex e ibiblio.

Gli utenti non dovrebbero in genere usare questo server a meno che abbiano bisogno di pacchetti src.rpm, pacchetti di debug o pacchetti che sono presi da uno specifico repository personale gestito dagli utenti.

I mirror dovrebbero inoltre evitare di sincronizzare da questo server poichè contiene molti più dati.

## Aggiungere gli URL alla nostra lista
* Mirmon: Comunica l'url del tuo mirror all'indirizzo email di contatto (la tua e-mail andrà probabilmente in moderazione, la prima volta). Noi l'aggiungeremo alle liste.
* Lista dei Media: per ogni release (cooker, 4.0, rock (4.1),rolling,...) il record è impostato come:

```
country=CountryName,city=CityName,latitude=[-]xx.y[y],longitude=[-]xx.y[y],bw=xxGB,version=VersionName,arch=ArchName,type=distrib,url=[ftp|http]://RootUrl/repository/ArchName
```

Per esempio:
```
country=Brasil,city=Curitiba,latitude=-13.58,longitude=-51.85,bw=1GB,version=2013.0,arch=x86_64,type=distrib,url=ftp://openmandriva.c3sl.ufpr.br/openmandriva/openmandriva2013.0/repository/x86_64/
```

Per favore manda anche i dettagli rilevanti del tuo mirror.

## Sincronizza il tuo mirror
* Puoi usare **rsync** (`man rsync` per più informazioni)

```
/usr/bin/rsync -av --delete --delete-delay --numeric-ids --delay-updates --exclude=.~tmp~/ mirror.rosalinux.com::openmandriva/ /your_path
```

> Dovresti usare `--delete-delay` e `--delay-updates`, come minimo.
{.is-warning}

* L'opzione ottimale sarebbe sincronizzare ogni 6 o 12 ore

\-
