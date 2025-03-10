---
title: Come cambiare il canale degli aggiornamenti
description: 
published: true
date: 2025-03-10T18:03:06.852Z
tags: documentation, howto, user-guide, advanced
editor: markdown
dateCreated: 2020-04-28T08:42:49.215Z
---

# Come cambiare il canale degli aggiornamenti
## Come passare da un sistema Rock a ROME (rolling)

Agli utenti che ancora non hanno familiarità con OpenMandriva consigliamo di iniziare con la versione stabile Rock per imparare come funziona il sistema e poi, se lo si desidera, di migrare a ROME, la rolling edition.

Un *utente ROME* dovrebbe essere in grado di usare la riga di comando e conoscere le basi del gestore di pacchetti [dnf](/en/distribution/guides/software-management/DNF).
Inoltre dovrebbe leggere e comprendere [OpenMandriva Release Plan and Repositories](/en/policies/release-plan-and-repositories).

Per aggiornare a ROME:

- Avvia il selettore di repositories Software Repository Selector (`om-repo-picker`) 
Menu delle Applicazioni > Software Repository Selector

![omlx43.doc.repopicker-01.jpg](/images/omlx43.doc.repopicker-01.jpg)

oppure seleziona OpenMandriva repo-picker in OM Welcome

![omlx43.doc.repopicker-02.jpg](/images/omlx43.doc.repopicker-02.jpg)


- Vai alla prima sezione 'Update channel'.

![om4.2-repopicker-03.jpg](/images/om4.2-repopicker-03.jpg)

- Scegli 'Rolling' dal menu a tendina.

![om4.2-repopicker-04.jpg](/images/om4.2-repopicker-04.jpg)

dai conferma cliccando su OK e quando ti viene richiesto inserisci la tua password di root. Questa operazione richiede un po' di tempo e la finestra del programma potrebbe diventare momentaneamente invisibile perciò attendi pazientemente.

Con questa azione avrai cambiato i repositori da Rock a Rolling quindi è bene fare un aggiornamento di sistema (`distro-sync`).

- Per aggiornare il tuo sistema apri Konsole (il terminale) e digita i seguenti comandi:
```
$ sudo dnf clean all ; dnf clean all ; dnf repolist
$ sudo dnf --allowerasing distro-sync
```

\-
