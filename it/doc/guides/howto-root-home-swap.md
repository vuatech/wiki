---
title: Come creare le partizioni root, home e swap durante l'installazione di OMLx
description: 
published: true
date: 2020-05-01T21:35:10.169Z
tags: documentation, howto, user-guide, advanced
---

# Come creare le partizioni root, home e swap durante l'installazione di OMLx

L'installer di OpenMandriva è  [Calamares](http://calamares.io/).
Facile da utilizzare, bello, pragmatico, inclusivo e  indipendente dalla distribuzione.
Calamares include una opzione per il partizionamento avanzato, che supporta sia il partizionamento manuale sia quello automatizzato.

> Nota: Quando leggi *Lx 4*, significa che include tutte le versioni 4.x come 4.0, 4.1, e 4.2. Questa guida è applicabile a tutte le versioni di OMLx incluse Cooker e Rolling come anche tutta la famiglia Lx 4.
{.is-info}

Puoi fare più o meno tutto ciò che ti serve per le partizioni scegliendo <kbd>Manual partitioning</kbd>

![root-home-swap-01.png](/images/root-home-swap-01.png)

Nota che accettando l'impostazione predefinita <kbd>Erase disk</kbd> sarà creata solo una partizione `/boot/efi` e una `/`
L'installer non crea più automaticamente una partizione di swap, perchè nella maggior parte dei moderni computer la swap non viene più usata.

Seleziona <kbd>Manual Partitioning</kbd>

![root-home-swap-02.png](/images/root-home-swap-02.png)

Vediamo come installare un sistema efi con partizioni `/` (root), `/home` e `swap` separate e la partizione `/boot/efi` necessaria per avviare un sistema efi. Se utilizzi una tabella di partizione MBR non hai bisogno di creare una partizione `/boot/efi`.
La partizione `/boot/efi` deve essere etichettata come `boot` (il partizionatore la etichetterà automaticamente come `esp`).

Il primo passo è selezionare <kbd>New Partition Table</kbd>

Se il sistema è efi o uefi boot bisogna usare una tabella delle partizioni di tipo GPT.
Se usi legacy boot puoi selezionare sia MBR che GPT. Se sei indeciso scegli `GPT` che è la più aggiornata. Inoltre se un utente ha più hard drive o SSD, essi devono avere tutti lo stesso tipo di tabella di partizionamento. Quindi o tutto `GPT` o tutto `MBR`

![root-home-swap-03.png](/images/root-home-swap-03.png)

Il passo successivo è creare `/boot/efi`, `/`, `/home`, e `swap`, in questo ordine.
E' importante che la prima partizione ad essere creata sia `/boot/efi`, le altre possono seguire nell'ordine che preferisci.

`/boot/efi` è tipicamente una partizione da 300 MB e deve essere fat16 or fat32 per funzionare. In alcuni installer il file system di questa partizione viene chiamato vfat.

Creare quindi le partizioni, una alla volta.
Seleziona <kbd>Create</kbd>

![root-home-swap-04.png](/images/root-home-swap-04.png)

Segui i passi nella finestra di dialogo, e alla fine ti troverai con qualcosa di simile

![root-home-swap-06.png](/images/root-home-swap-06.png)

Quando sei soddisfatto fai click su <kbd>Next</kbd> e una volta installato il tuo nuovo sistema avrà le partizioni di root, home e swap separate.

Nota che `/boot/efi` è in cima alla lista al primo posto. Questo è indispensabile.

> Nota che la tua partizione di swap probabilmente non verrà mai utilizzata. Solo una piccola minoranza di utenti hanno veramente bisogno di una partizione di swap. Coloro a cui serve davvero ne sono già a conoscenza. Di solito la swap serve a computer molto vecchi che non hanno abbastanza RAM per far funzionare Lx 4.
Quanta RAM occorre? Idealmente 4 GB. Noi abbiamo utenti che usano Lx 4 con 2 GB. Le note di rilascio per Lx 4.0 e 4.1 dicono 2 GB e l'installer Calamares richiede 2 GB.  Aggiornare la quantità di memoria in un computer, che sia un desktop, laptop o notebook è semplice ed economico al giorno d'oggi. Quindi se il tuo computer ha poca memoria RAM considera di aumentarla.
La swap può essere ancora utilizzata in alcuni computer che fanno calcoli scientifici e matematici ad un livello molto intenso o che magari utilizzano pesanti applicazioni grafiche. Ma come già detto questo tipo di utenza sa di cosa ha bisogno.
{.is-info}

Questo è uno screenshot di come la finestra di dialogo <kbd>Create</kbd> dovrebbe apparire per la tua partizione `/boot/efi`  in un sistema UEFI/EFI:

![root-home-swap-05.png](/images/root-home-swap-05.png)

\-