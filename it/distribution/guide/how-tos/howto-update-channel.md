---
title: Come cambiare il canale degli aggiornamenti
description: 
published: true
date: 2020-12-21T23:54:10.640Z
tags: 
editor: undefined
dateCreated: 2020-05-02T17:24:57.250Z
---

# Come cambiare il canale degli aggiornamenti
## Come passare da Rock a Rolling

Se sei un nuovo utente di OpenMandriva Lx ti suggeriamo di iniziare con la release Rock che è molto stabile in modo da poter imparare come funziona il sistema, poi se lo desideri puoi passare alla versione Rolling.

Un utente 'Rolling' dovrebbe sapere usare la linea di comando e conoscere le basi del gestore di pacchetti [dnf](/en/doc/using-dnf).
Inoltre l'utente ha bisogno di leggere e capire [Piano di rilascio e repository](/en/doc/release-plan-and-repositories).

Per aggiornare a rolling:

- Avvia il selettore di repositories Software Repository Selector (`om-repo-picker`) 

Menu delle Applicazioni > Software Repository Selector

![repositories01.jpg](/images/repositories01.jpg)

Puoi trovare l'applicazione anche nella schermata di benvenuto di OpenMandriva.

![repositories07.jpg](/images/repositories07.jpg)

- Vai alla prima sezione 'Update channel'.

![repositories02.jpg](/images/repositories02.jpg)

- Scegli 'Rolling' dal menu a tendina.

![update-channel-rolling.jpg](/images/update-channel-rolling.jpg)

dai conferma cliccando su OK e quando ti viene richiesto inserisci la tua password di root. Questa operazione richiede un po' di tempo perciò attendi pazientemente.

Con questa azione avrai cambiato le repositories da Rock a Rolling quindi è bene fare un aggiornamento di sistema (`distro-sync`).

- Per aggiornare il tuo sistema apri Konsole (il terminale) e digita i seguenti comandi:
```
$ sudo dnf clean all ; dnf clean all
$ sudo dnf --allowerasing distro-sync
```

\-

