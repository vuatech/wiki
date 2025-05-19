---
title: Come configurare la stampante in OMLx
description: 
published: true
date: 2025-05-03T15:56:07.005Z
tags: documentation, howto, user-guide
editor: markdown
dateCreated: 2020-03-09T18:43:12.417Z
---

# Come configurare la stampante
Accendi la stampante e controlla se è configurata automaticamente. Controlla se è stato installato il driver giusto.

Se la stampante è stata configurata automaticamente e mostra il driver corretto, sei a posto.

Se non lo fosse, spegni la stampante.

Verifica che il pacchetto `system-config-printer` sia installato.
Apri *Impostazioni della stampante* con `kcmshell6 kcm_printer_manager` (`kcmshell5` per Plasma5), e rimuovi la stampante.
Se il driver corretto non è stato installato automaticamente, dovrai installare un pacchetto supplementare.

Il prossimo passo è capire qual è il pacchetto da installare.

In OpenMandriva Lx è molto probabile che sia un pacchetto `task-printing` specifico per la marca della tua stampante. I pacchetti sono:
- task-printing-canon
- task-printing-epson
- task-printing-hp
- task-printing-lexmark
- task-printing-okidata
- brlaser (per stampanti Brother)
- task-printing-misc

Installa il pacchetto che corrisponde alla marca della tua stampante, oppure il pacchetto `task-printing-misc` se nessuno di essi corrisponde.

Esempio utilizzando okidata:
```
$ sudo dnf install task-printing-okidata
```
Ora riaccendi la stampante, che dovrebbe configurarsi automaticamente (potrebbe essere necessario un riavvio per far funzionare la configurazione automatica).

Altrimenti chiedi aiuto qui [here](https://forum.openmandriva.org/c/support/17)
