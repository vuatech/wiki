---
title: OpenMandriva Repositories tl;dr
description: 
published: true
date: 2020-07-27T17:43:16.854Z
tags: documentation, user-guide
editor: markdown
---

# Sorgenti Media
## Abbiamo quattro sorgenti media di base: `/main`, `/unsupported`, `/restricted` e `/non-free`.
Come gestire i repository con om-repo-picker
#### Menu delle applicazioni > Selettore dei repository Software Repository Selector (om-repo-picker)

![repositories01.jpg](/images/repositories01.jpg)

Oppure puoi lanciare Software Repository Selector nella schermata di benvenuto di OpenMandriva.

![repositories07.jpg](/images/repositories07.jpg)

main

### `/main` contiene i pacchetti core del sistema mantenuti dal team di OpenMandriva Lx.
Esso include tutto quello che c'è nell'immagine di installazione insieme ad alcune applicazioni che sono considerate importanti. `/main/release` dovrebbero sempre essere abilitati.
![repositories02.jpg](/images/repositories02.jpg)

**Per l'uso comune gli utenti non dovrebbero mai abilitare i repository** `/testing` **nella release stabile**.

![repositories02x.jpg](/images/repositories02x.jpg)

unsupported

### `/unsupported` rappresenta i pacchetti mantenuti dalla comunità.
Non sono supportati dal team OpenMandriva e sta ai mantenitori di questi pacchetti se aggiornarli o meno.
Ci possono essere molti pacchetti utili e aggiornati, così come molti che non si installano o altri che si installano ma non funzionano correttamente. Gli utenti sono liberi di utilizzare qualsiasi cosa che verificano sia funzionante in questo repository.
Come abilitare il repository unsupported con om-repo-picker
#### ![repositories03.jpg](/images/repositories03.jpg)

restricted

### `/restricted` contiene librerie che non sono installate di default per motivi di carattere legale come ad esempio problemi con le licenze.
Il permesso di usare questi pacchetti varia a seconda delle leggi locali. OpenMandriva non può essere ritenuta responsabile per il loro utilizzo!
**Se credi che il loro utilizzo sia proibito nel tuo paese, disabilita le repository restricted.**
Come abilitare il repository restricted con om-repo-picker
#### ![repositories04.jpg](/images/repositories04.jpg)

non-free

### `/non-free` contiene applicazioni e driver che sono distribuiti, ma non soddisfano la definizione di Software Libero [Free Software](https://en.wikipedia.org/wiki/The_Free_Software_Definition). Noi possiamo aggiustare i pacchetti di queste applicazioni, ma **non abbiamo accesso al codice sorgente di conseguenza non possiamo correggere i problemi causati dai file presenti in questo repository**.
Come abilitare il repository non-free con om-repo-picker
#### ![repositories05.jpg](/images/repositories05.jpg)

> Per favore nota che in OMLx 4.1 per alcune applicazioni, come ad esempio Steam, sarà necessario abilitare **sia `non-free` che `main 32bit`**
{.is-info}

![repositories06.jpg](/images/repositories08.jpg)


Dopo le modifiche

## Quando hai finito di applicare le modifiche, lancia il seguente comando nel terminale
`$ sudo dnf clean all ; dnf clean all ; dnf repolist`
Leggi di più

## Per una spiegazione dettagliata leggi  [Piano di Rilascio e Repository](/doc/release-plan-and-repositories)
\-
