---
title: Piano di Rilascio e Repository
description: 
published: true
date: 2021-09-26T22:17:55.824Z
tags: documentation
editor: markdown
dateCreated: 2020-05-02T19:51:47.899Z
---

# OpenMandriva Piano di Rilascio e Repository

Prima di fare qualsiasi cambiamento che riguardi la release o i canali di aggiornamento se sei anche solo leggermente insicuro fermati, non farlo, piuttosto chiedi consiglio sul nostro forum o nella chat con il Team di OpenMandriva.

## Release
Una release è un gruppo di pacchetti software che messi assieme formano un sistema operativo.
Ogni release è distinta dalla sua "versione", come *Mandriva 2009*, *Windows XP*, *OpenMandriva Lx 2014*, *OpenMandriva Lx 4.0*, ecc.
Le release sono anche chiamate *Canali di Aggiornamento*.
Release, Rock, Rolling e Cooker sono tutte diverse versioni di rilascio/canali di aggiornamento di OpenMandriva Lx. L'enfasi va sulla parola 'diverse'.
**Esse non vanno mai mischiate fra di loro**.

## Repositories
I repository sono server che contengono dei pacchetti, che letteralmente sono dei file .rpm.
Nel sistema operativo OpenMandriva il software è impacchettato in file .rpm che contengono i programmi e le librerie che ti servono. Questi file possono essere scaricati e alcuni sono inclusi nei file .iso come specifiche "versioni di rilascio" per l'installazione da parte dell'utente.
Ogni release di OpenMandriva ha le sue repository.
Queste repository non sono intercambiabili, **non mischiarle**.
Gli utenti generalmente accedono a questi file con strumenti per la gestione dei pacchetti come [DNF](/en/doc/using-dnf), o precedentemente URPM.
Ci sono anche strumenti ad interfaccia grafica come dnfdragora, Discover e precedentemente RpmDrake.

## Piano di Rilascio
Il "Piano di Rilascio", anche conosciuto come "Canale di Aggiornamento", è una gerarchia di pacchetti software raggruppati assieme (versioni di rilascio) per un determinato scopo.
Per esempio il canale di aggiornamento Cooker è progettato apposta per gli sviluppatori che possono lavorarci anche se dovessero "guastare" qualcosa.
Un altro esempio è il canale di aggiornamento Rock che è progettato per utenti comuni che usano il computer per compiti giornalieri ed è progettato per non rompersi (letteralmente progettato per essere "stabile").

Con OpenMandriva Lx 4.0, la distribuzione ha implementato un nuovo piano di rilascio in modo da organizzare meglio il ritmo di lavoro per il mantenimento dei pacchetti e per la modernizzazione e velocizzazione del processo di rilascio. Ciò è strettamente coordinato con la struttura dei nostri repository.
Su un sistema bisogna usare solo una release. **Non mischiare releases/canali di aggiornamento altrimenti i conflitti tra i pacchetti sono probabili se non garantiti**.

Le release sono anche conosciute come "Canali di Aggiornamento". Ogni versione ha i suoi repository. I repository o file .repo si trovano nella directory `/etc/yum.repos.d`. Dal nome dei repository, i loro nomi sono rispettivamente openmandriva-cooker, openmandriva-rolling, openmandriva-rock e openmandriva-release.
I repository sono ulteriormente definiti e nominati per architettura. Esempio qui sotto.

- **Cooker (Instabile)**

Cooker è il ramo di sviluppo. Qui è dove gli sviluppatori fanno il loro lavoro di sviluppo dei pacchetti e della distro in generale. A causa della natura di questo lavoro continuativo Cooker a volte si guasta. Questo è corretto.
Noi non stiamo dicendo che Cooker *potrebbe guastarsi*, stiamo dicendo onestamente che Cooker *si guasterà*.
Se non sei abituato ad operazioni di risoluzione dei problemi con il computer ad livello molto avanzato allora cooker non fa per te.

- **Rolling**

La Rolling release è ancora in fase di sviluppo e non è stata ancora annunciata ufficialmente.
Per adesso l'intera Rolling release sta venendo testata e non è ancora pronta per l'uso produttivo.

Rolling è dove gli sviluppatori prendono pacchetti quando credono che siano pronti all'uso.
Come suggerisce il nome, è una rolling release e quindi avrà tutti i pacchetti più aggiornati.
Rolling è progettata per essere un sistema utilizzabile e che funziona. Gli utenti rolling devono essere in grado di gestire alcuni problemi da soli come con qualsiasi release "Bleeding Edge". Inoltre gli utenti 'Rolling' dovrebbero avere familiarità ed essere capaci di usare la linea di comando o terminale (Konsole) se occorre.

-   **Rock (Stabile)**

Le repository Rock consistono in un link simbolico all'ultima versione stabile di OpenMandriva.
Attualmente Rock è collegata a OM Lx 4.1. In seguito, quando OMLx 4.2 verrà rilasciata, Rock sarà automaticamente migrata a OMLx 4.2.

-   **Release (Stabile)**

Le repositories Release sono le ultime versioni stabili di OpenMandriva Lx attualmente OMLx 4.0 e 4.1. Le repository Release sono collegate alla release stessa. Se installi OMLx 4.0 e usi la repository Release invece che quella Rock rimarrai con le repository 4.0.
La versione Release/Stabile è la più stabile di tutte ed è pefetta per gli utenti a cui piace che le cose stiano come sono e che funzionino e basta. Gli aggiornamenti per i pacchetti saranno limitati alle correzioni di bug e agli aggiornamenti di sicurezza.
Tieni a mente che ogni versione raggiungerà la EOL (acronimo che significa "Fine della Vita") e da li in poi non ci saranno più aggiornamenti di alcun tipo.
Inoltre ricordati: Su un dato sistema bisogna usare soltanto una data release.
**Non mischiare release/canali di aggiornamento altrimenti i conflitti tra pacchetti saranno molto probabili se non garantiti**.

Il flusso di lavoro dei pacchetti è:
`Cooker/Unstable > Rolling > Release/Stable`
*Ricordati che Rock è un symlink all'ultima release stabile*

## Lista dei file della repository

Esempio usando OMLx x86_64
*gli utenti znver1 vedranno znver1 invece di x86_64*

Ogni release ha i propri repository. Non sono interscambiabili, non mischiarli.

Questi sono i file dei repository per OpenMandriva Lx x86_64.
I file i686 sono presenti solo per l'occasionale installazione di applicazioni a 32 bit come Wine, Steam oppure altre applicazioni per i giochi.
E' fortemente consigliato di abilitarle solo per installare e aggiornare quegli specifici pacchetti , in tutti gli altri casi lasciali disabilitati. Altrimenti strani, sconcertanti e imprevisti problemi potrebbero presentarsi.
Tieni a mente che ogni sviluppatore che continua a sviluppare *solo* per 32 bit è monumentalmente indietro con i progressi tecnici di Linux.

I file dei repository in ordine alfabetico come sono nel sistema dell'utente

- **Cooker (Unstable)**

`openmandriva-cooker-i686.repo`
`openmandriva-cooker-i686-source.repo`
`openmandriva-cooker-x86_64.repo`
`openmandriva-cooker-x86_64-source.repo`

- **Release (Stable)**

`openmandriva-release-i686.repo`
`openmandriva-release-i686-source.repo`
`openmandriva-release-x86_64.repo`
`openmandriva-release-x86_64-source.repo`

- **Rock (symlink to latest Stable)**

`openmandriva-rock-i686.repo`
`openmandriva-rock-i686-source.repo`
`openmandriva-rock-x86_64.repo`
`openmandriva-rock-x86_64-source.repo`

- **Rolling ("Bleeding Edge")**

`openmandriva-rolling-i686.repo`
`openmandriva-rolling-i686-source.repo`
`openmandriva-rolling-x86_64.repo`
`openmandriva-rolling-x86_64-source.repo`

*gli utenti znver1 vedranno znver1 invece di x86_64*

Gli utenti di norma non usano file source.repo. Se non hai motivo di usarli, non usarli.

## File di repository che vengono normalmente utilizzati

Per farla breve la stragrande maggioranza degli utenti x86_64 normalmente userà **soltanto uno** di questi quattro file

File dei repository elencati in ordine dalla più stabile alla meno stabile:

`openmandriva-release-x86_64.repo`
`openmandriva-rock-x86_64.repo`
`openmandriva-rolling-x86_64.repo`
`openmandriva-cooker-x86_64.repo`

*gli utenti znver1 vedranno znver1 invece di x86_64*

## Fonti media

In ogni file di repository elencato sopra abbiamo quattro fonti media di base o categorie:

- **main**

`/main` contiene i pacchetti core del sistema mantenuti dal team di OpenMandriva Lx. Esso include tutto quello che c'è nell'immagine di installazione insieme ad alcune applicazioni che sono considerate importanti. I repository di /main/release dovrebbero essere sempre attivati. Se il tuo sistema usa i file dei repository Release o Rock, allora /main/release/updates dovrebbero sempre essere abilitati.

- **unsupported**

`/unsupported` rappresenta i pacchetti *mantenuti dalla comunità*. Non sono supportati dal team OpenMandriva e sta ai mantenitori di questi pacchetti se aggiornarli o meno. Ci possono essere pacchetti che non si installano e altri che riescono ad essere installati però non funzionano correttamente. Gli utenti sono liberi di utilizzare qualsiasi cosa che verificano sia funzionante in questo repository.

- **restricted**

`/restricted` contiene librerie che non sono installate di default per motivi di carattere legale come ad esempio problemi con le licenze.
Il permesso di usare questi pacchetti varia a seconda delle leggi locali. OpenMandriva non può essere ritenuta responsabile per il loro utilizzo!
**Se credi che il loro utilizzo sia proibito nel tuo paese, disabilita le repository restricted.**

- **non-free**

`/non-free` contiene applicazioni e driver che sono distribuiti, ma non soddisfano la definizione di Software Libero [Free Software](https://en.wikipedia.org/wiki/The_Free_Software_Definition). Noi possiamo aggiustare i pacchetti di queste applicazioni, ma **non abbiamo accesso al codice sorgente di conseguenza non possiamo correggere i problemi causati dai file presenti in questo repository**.

## Spiegazione di cosa abilitare nelle categorie dei repository

Puoi abilitare tutto ciò che segue con il Selettore di repository Software Repository Selector (om-repo.picker) nel menu delle Applicazioni sotto la categoria 'Sistema'.
Una guida per farlo è disponibile [qui](https://forum.openmandriva.org/t/2726).

In pratica ogni categoria di Release scelta dovrebbe sempre abilitare il repository Main. Per Release (Stabile) e Rock (Stabile) devono essere abilitati (usando sistemi x86_64 come esempio)

`/x86_64/main/release/`
`/x86_64/main/updates/`

*gli utenti znver1 vedranno znver1 invece di x86_64*

La scelta se usare tutti o alcuni dei repository Unsupported, Restricted, o Non-Free è una decisione propria dell'utente però in tal caso dovresti abilitare sia /release che relativi /updates. 

`/x86_64/unsupported/release/`
`/x86_64/unsupported/updates/`
`/x86_64/restricted/release/`
`/x86_64/restricted/updates/`
`/x86_64/non-free/release/`
`/x86_64/non-free/updates/`

*gli utenti znver1 vedranno znver1 invece di x86_64*

Rolling e Cooker si differenziano nel senso che non c'è alcuna categoria update relativa quindi non tenere in considerazione i riferimenti a /updates dalla lista sopra.

Per chiarire meglio, per quanto riguarda Release/Stable e Rock verrebbero abilitati a seconda 2, 4, 6, fino ad un massimo di 8 categorie di media.
Per Rolling o Cooker invece da 1 fino ad un massimo di 4 categorie di media. Ciò si applica a circostanze normali.

