---
title: Strumento Bug report per OpenMandriva Lx
description: 
published: true
date: 2025-02-03T06:23:07.932Z
tags: documentation, user-guide, tools
editor: markdown
dateCreated: 2021-03-10T16:47:18.423Z
---

# Strumento Bug report per OpenMandriva Lx
Un semplice strumento chiamato omv-bug-report.

## Le scorciatoie
### Aprire OM Welcome e raggiungere la schermata OM Features > *Bug report tool*

![om-bugreportwelc.jpg](/images/om-bugreportwelc.jpg)

### Oppure aprire OpenMandriva Control Center e raggiungere la schermata System > *Bug report tool*

![om-bugreportomcc.jpg](/images/om-bugreportomcc.jpg)

## Informazioni raccolte
Lo strumento raccoglie informazioni utili da:

- vari file di configurazione (in /etc/*)
- varie stringhe da /proc (informationi sul kernel)
- grub configuration (il programma di avvio)
- lspcidrake output (lista dei dispositivi PCI)
- lsusb output (lista dei dispositivi USB)
- dmidecode output (informazioni sull'hardware dal BIOS)
- systemctl –failed (per il rapporto del mancato avvio del sistema o dei servizi)
- journalctl -b (mostra il log dell'avvio attuale)
- rpm -qa (una lista dei pacchetti installati)
- gcc version (la versione del compilatore)

![om-bugreportpopup.jpg](/images/om-bugreportpopup.jpg)

Quindi verrà creato un archivio omv-bug-report.log.zst contenente tutti i dati nella directory /home dell'utente

![om-bugreportfile.jpg](/images/om-bugreportfile.jpg)

> **Tale file dovrà essere allegato ad ogni segnalazione di bug**
{.is-info}

Ciò aiuta e velocizza il lavoro di correzione dei bug e semplifica il lavoro della persona che segnala il bug fornendo informazioni dettagliate.

Leggere il contenuto del file

Il file è compresso con zst. E' possibile estrarre l'archivio e leggere il suo contenuto mediante il comando `unzstd`


