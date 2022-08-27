---
title: Politiche dei Repository
description: 
published: true
date: 2021-09-26T21:17:05.607Z
tags: policies, cooker, qa
editor: markdown
dateCreated: 2020-05-06T09:36:21.786Z
---

# Politiche dei Repository

## Cooker
Cooker è un ramo sperimentale che ogni tanto può guastarsi.

Fare modifiche in questo ramo va bene nella maggior parte dei casi, anche aggiornare ad una versione beta o perfino ad uno snapshot git/svn/cvs/hg di un pacchetto dalla fonte principale.

Per essere sicuri di non "fare sorprese" altri altri sviluppatori guastando tutto, i cambiamenti principali devono essere coordinati. Si può fare in vari modi:
- parlarne in un TC meeting
- inviare una pull request nel relativo repository e attendere l'accettazione
- mandare una email alla mailing list cooker e aspettare le risposte positive degli altri membri

Le modifiche che richiedono la coordinazione includono, ma non sono limitati a:
- cambiare un componente principale di sistema con qualcosa di diverso (ad esempio cambiare Xorg con Wayland, Qt 5 con Qt 6, wpa_supplicant con iwd, systemd con qualsiasi altro sistema di init, ecc.); ogni cambiamento del genere dovrebbe essere prima testato in un repository personale.
- aggiornamenti che richiedono una quantità enorme di rebuild (es. aggiornare libpng a una versione con un nuovo *soname*).
- rimuovere un pacchetto largamente utilizzato da molti elementi nel sistema (es. rimuovere qt5 al momento dell'uscita di qt6 stabile)
- cambiamenti che potrebbero rovinare l'hardware

Cooker è di solito aperto a qualsiasi tipo di sviluppo, ma talvolta può essere congelato in modo da concentrare tutti gli sforzi su un solo ramo.

## Rolling
Normalmente Rolling deve sempre essere utilizzabile. Elementi che potrebbero guastare il sistema in maniera rilevante non possono andare nel repository Rolling.

Per essere sicuri che Rolling sia sempre utilizzabile:
- Qualsiasi cosa pubblicata nel repo Rolling deve essere prima compilata per Cooker.
Eccezione: qualcosa di cui Cooker ha già una versione più recente, ad esempio può avere senso spingere LLVM 8.0.1 in Rolling se Rolling è a 8.0 anche quando Cooker è già alla versione 9.0.
- Gli sviluppatori devono pubblicare i pacchetti in `rolling/testing` -non in `rolling/release` - quando ritengono che qualcosa sia pronto per l'uso generale. Spostare materiale da `rolling/testing` a `rolling/release` è compito del QA (coloro che assicurano la qualità), per essere sicuri che i pacchetti siano testati nell'ambiente Rolling.
- Rolling non dovrebbe di norma utilizzare release beta/snapshots della fonte principale del software. Ci sono eccezioni a questa regola, ad esempio quando il sorgente non ha più rilasciato aggiornamenti uno snapshot/beta è l'unica cosa che funziona nel nostro ambiente, ad esempio la release "stable" usa ancora Qt 4 o Python 2, oppure ci sono altre buone ragioni.
Rolling viene congelata poco prima di una nuova release, in modo che le release possano essere fatte essenzialmente come degli snapshot di rolling/release.

## Rock
Questo è il ramo di release stabile. Esso riceverà solo gli aggiornamenti importanti, come aggiornamenti sicurezza o correzionii per i crash di sistema.

Le persone che vogliono le versioni più aggiornate del software dovrebbero usare Rolling invece di Rock.
Ciò significa che gli utenti che usano Rock vogliono qualcosa che non si guasta mai. Ogni cambiamento in Rock deve essere valutato con la massima attenzione.
- Qualsiasi cosa pubblicata nel repo Rock deve essere prima compilata per Rolling.
Eccezione: Qualcosa di cui cooker ha una versione più recente, ad esempio può avere senso spingere LLVM 8.0.1 in Rock se Rock è a 8.0 anche se Rolling è già alla versione 0.9.
- Gli sviluppatori devono pubblicare i pacchetti in `rock/testing` - non in `rock/release` - quando ritengono che qualcosa sia pronto per l'uso generale. Spostare materiale da `rock/testing` a `rock/release` è compito del QA (coloro che assicurano la qualità), per essere sicuri che i pacchetti siano testati nell'ambiente Rock.
- Rock non dovrebbe di norma utilizzare release beta/snapshots della fonte principale del software. Fai ancora più attenzione di quanto lo hai fatto per Rolling. Ci sono eccezioni a questa regola, ad esempio quando il sorgente non ha più rilasciato aggiornamenti uno snapshot/beta è l'unica cosa che funziona nel nostro ambiente, ad esempio la release "stable" usa ancora Qt 4 o Python 2, oppure ci sono altre buone ragioni.
- Gli aggiornamenti non dovrebbero modificare l'interfaccia dell'utente. Le persone che utilizzano Rock vogliono qualcosa di familiare e non vogliono sorprese.
- **Se sei in dubbio, non farlo**. Le persone che vogliono aggiornare qualcosa di non importante dovrebbero usare Rolling.



