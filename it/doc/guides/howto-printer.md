---
title: Come configurare la stampante in OMLx
description: 
published: true
date: 2020-04-23T20:06:22.317Z
tags: documentation, howto, user-guide
---

# Come configurare la stampante in OMLx
Accendi la stampante e controlla se è configurata automaticamente. Controlla se è stato installato il driver giusto.

Se la stampante è stata configurata automaticamente e si dispone del driver corretto, sei a posto.

Se non lo fosse, spegni la stampante.

Apri *Impostazioni della stampante* aka `system-config-printer` , e rimuovi la stampante.
Se il driver corretto invece non è stato installato automaticamente, dovrai installare un pacchetto supplementare.

In OpenMandriva Lx molto probabilmente sarà un pacchetto "task-printing" specifico per la tua stampante.
I pacchetti sono:
- task-printing-canon
- task-printing-epson
- task-printing-hp
- task-printing-lexmark
- task-printing-okidata
- task-printing-misc

Installa il pacchetto che corrisponde alla marca della tua stampante, oppure il pacchetto `task-printing-misc` se nessuno di essi corrisponde.

Esempio utilizzando okidata:
```
$ sudo dnf install task-printing-okidata
```
Ora riaccendi la stampante, che dovrebbe quindi configurarsi automaticamente (a volte potrebbe essere necessario un riavvio).

In caso di necessità puoi chiedere aiuto [qui](https://forum.openmandriva.org/c/en/support)


