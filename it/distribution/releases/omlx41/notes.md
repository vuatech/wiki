---
title: OpenMandriva Lx 4.1 Note di rilascio
description: 
published: true
date: 2021-09-26T21:02:54.401Z
tags: 4.1
editor: markdown
dateCreated: 2020-02-28T12:18:34.424Z
---

# OpenMandriva Lx 4.1 Note di rilascio
Il Team di OpenMandriva Lx è lieto di annunciare la disponibilità di **OpenMandriva Lx 4.1**. [Codename](/en/releases/codename) Mercury

## Available Media

Questa release è disponibile come live media DVD o USB flash drive (chiavetta di memoria), scaricabile in formato ISO file. Si possono trovare alla nostra [pagina downloads](https://www.openmandriva.org/en/download). L'installazione da chiavetta USB è di solito notevolmente più veloce. Come sempre, la velocità dipende da molti fattori.
*Live media* significa che potrai avviare OpenMandriva Lx direttamente da DVD o memory stick (vedi in seguito) e provare il sistema prima di installare.

Immagini ISO disponibili:
- [KDE Plasma](https://www.kde.org/plasma-desktop) desktop completo (include una vasta scelta dei programmi più usati, multimedia e software per l'ufficio).
- znver1 Plasma: inoltre abbiamo una versione specifica per i moderni processori AMD (Ryzen, ThreadRipper, EPYC) che ha una performance superiore a quella della versione generica (x86_64) sfruttando le nuove funzionalità di questi processori.
znver1 è disponibile solamente per i seguenti processori (Ryzen, Thread Ripper, EPYC), non installare su nessun altro tipo di hardware.

## Raccomandazioni per l'Hardware

OpenMandriva Lx4.1 richiede un minimo di 2.0 GB di memoria e almeno 10 GB di spazio su disco fisso (guarda sotto per problemi di partizionamento già rilevati).

> Nota importante: Hardware Grafico:
> Il desktop KDE Plasma richiede una scheda grafica che supporti OpenGL 2.0 o superiore.
> Raccomandiamo di utilizzare schede grafiche  AMD, Intel, Adreno o VC4.
{.is-warning}


## Connessione Internet

L'installer Calamares controlla se c'è una connessione internet disponibile, ma OpenMandriva Lx 4 verrà installato senza problemi anche senza connessione. Installa come faresti normalmente e procedi ad utilizzare il sistema. E' perfettamente OK.
Aggiornare un sistema del genere richiederà di essere temporaneamente connessi a internet oppure si possono scaricare i pacchetti in un altro sistema e trasferirli al sistema installato e procedere a installare i pacchetti aggiornati.
Ma fino a che non  si è connessi a internet si può semplicemente usare il sistema senza aggiornarlo per quanto vogliamo.

## Macchine Virtuali
Per ora l'unico software di virtualizzazione su cui le ISO di OMLx sono state testate è VirtualBox. I requisiti hardware sono gli stessi anche quando si sta usando una macchina virtuale.
Per quanto riguarda VirtualBox dovrai impostare un minimo di 2048 MB di memoria altrimenti OpenMandriva fallirà il processo di boot.
Ancora per quanto riguarda VirtualBox è consigliato installare in una macchina virtuale nuova, perchè provare a installare il sistema in una già esistente potrebbe occasionalmente non funzionare.

## Installer Calamares

Calamares è un installer strutturale.
Da design è molto personalizzabile in modo da soddisfare un'ampia varietà di casi e bisogni. L'obiettivo di questo installer è essere facile da usare, bello, pragmatico, inclusivo e indipendente dalla distribuzione.
Calamares include un'opzione per il partizionamento avanzato, che supporta sia operazioni di partizionaamento manuale sia operazioni di partizionamento automatizzato.
Questo è il primo installer con un'opzione automatizzata "Rimpiazza Partizione", che rende semplice il riutilizzo di una partizione per necessità di distribution testing.
Tante distribuzioni Linux usano Calamares come installer e ciascuna ha la sua implementazione e i suoi standard. Il fatto che qualcosa nell'installer di OpenMandriva non si conforma all'esperienza dell'utente con altre distribuzioni Linux non significa che quel qualcosa sia un bug.

## Partizionamento

Per ora il partizionamento LVM e i setup Raid con l'installer Calamares non sono supportati. **Ciò si applica a tutti i partizionamenti**, tutte le installazioni su hardware: Se possiedi un computer con sistema UEFI/EFI e il tuo BIOS offre una scelta al momento del boot ad esempio:

`Chiavetta USB`
`Chiavetta USB UEFI`
o 
`supporto DVD`
`supporto DVD UEFI`

in questi casi devi avviare scegliendo l'opzione UEFI. Ma sappi che non tutti i computer sono uguali. Alcuni con BIOS più spartane offriranno solo un opzione e quasi sempre sarà quella corretta. Quindi per esempio se su un notebook non vedi le possibilità descritte sopra non preoccuparti. Se hai unità di memoria multiple ciò che devi fare è avere lo stesso tipo di tabelle di partizionamento. Devono essere o tutte gpt o tutte mbr per fare si che tutto funzioni correttamente.
Su sistemi UEFI in situazioni di multi-boot con unità di memoria multiple se si ha già una partizione `/boot/efi` esistente bisogna usare quella. Il partizionatore non creerà un'altra partizione `/boot/efi` con flag appropriate e quindi l'installazione risulterà in un errore di bootloader non installato. Non formattare, devi solo impostare il punto di mount a `/boot/efi`. Si possono avere tanti bootloader per sistemi operativi diversi nella stessa partizione `/boot/efi`. Se c'è bisogno di cambiare bootloader, si fa nelle impostazioni del BIOS.

## NVME SSDs

Alcune SSD NVME potrebbero non essere riconosciute dalla live ISO di OMLx4.1.
La *Live* ISO ha 2 stratagemmi per questo sotto "Troubleshooting" nel menu di Grub2.
Sono `(PCIE ASPM=OFF)` e `(NVME APST=OFF)`. Confidiamo che funzioni per l'hardware della maggior parte delle persone. Il problema è conosciuto e gli sviluppatori di OMLx4 ci stanno lavorando. Vedi di più in [4.1/Errata](/releases/omlx41/errata#nvme-ssds).
La release di OMLx4.1 include kernel 5.5.0 e riconoscimento hardware per SSD NVME dovrebbe essere considerevolmente migliorato. Ci risulta che alcune SSD NVME che nella versione precedente non erano riconosciute con questa versione del kernel ora lo sono. Questo problema è molto specifico per alcuni tipi di hardware particolare.

## Installer e Supporto EFI

Questa release di OpenMandriva Lx supporta il boot e l'installazione con e senza  [UEFI](https://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface).
Si noti che il secure boot NON è supportato.
Se si desidera effettuare un installazione EFI su un disco MBR già esistenete sarà necessario convertire la tabella delle partizioni presente sul disco usando lo schema di partizionamento GPT. Per fare ciò è necessario utilizzare il programma gdisk. Una tipica invocazione potrebbe essere gdisk `gdisk /dev/sda` : la partizione esistente verrà convertita in schema GPT in memoria.Attenzione che facendo ciò potrebbe verificarsi una perdita di dati, il disco non sarà alterato fino a che la tabella delle partizioni viene scritta premendo il tasto <kbd>w</kbd>. Consigliamo di effettuare sempre un backup dei tuoi dati importanti prima di procedere con questo tipo di operazioni.
Potrebbero esserci occasioni nelle quali la conversione non può essere effettuata, ciò è solitamente dovuto a spazio insufficiente per scrivere la tabella delle partizioni all'inizio o alla fine del disco. Potrebbe essere necessario eliminare oppure ridimensionare una partizione per fare spazio, gparted è il tuo migliore amico in queste circostanze.
Occorre creare una partizione efi per contenere l'equipaggiamento di boot, questa partizione va creata mentre si usa l'installer Calamares. Quando l'installer raggiunge il momento del partizionamento la partizione di root (/) dovrebbe essere rimossa e una piccola partizione da 330MB in FAT32 o FAT16 deve essere creata all'inizio del disco. Se lo spazio su disco è critico si può usare una partizione più piccola ma bisogna assicurarsi che sia impostata come FAT16 o FAT32 in Calamares altrimenti l'installazione non andrà a buon fine.
Se non seguirai queste indicazioni l'installazione del boot loader fallirà. Successivamente partiziona il disco in maniera normale.
Per favore condividete le vostre esperienze nei forum così che noi abbiamo modo di migliorare questo aspetto dell'installazione.
Se stai installando in dual booting con Windows 8, 8.1, 10 o altri sistemi operativi EFI, come precauzione per favore assicurati di avere dischi di recupero e di avere un backup dei tuoi dati importanti. 
Il nostro testing è stato limitato con questa configurazione, ma sono stata effettuate installazioni con successo senza problemi.
Ogni tipo di feedback che riguarda quest'area è bene accetto.

## Cambiare tipo di partizione 

Per favore nota che Calamares non può convertire da un tipo di partizione a un'altra e conservare i dati delle partizioni.
Se fai partire Calamares in Live non è possibile cambiare il tipo di partizione di una partizione esistente. Se provi ad eseguire questa operazione, ti apparirà un messaggio di errore.
Perchè vada a buon fine, devi prima eliminare la partizione e crearne una nuova con il tipo di partizione desiderato.

## File system raccomandati per installazione manuale

Fortemente raccomandato è il file system [ext4](https://en.wikipedia.org/wiki/Ext4) perchè con ext4 sono stati rilevati meno problemi e questo filesystem funziona su una grande varietà di hardware.
Per unità di memoria flash memory-based (in pratica le SSD) rendiamo disponibile [F2FS](https://en.wikipedia.org/wiki/F2FS) e i riscontri sono per lo più positivi.
Alcuni utenti vorrebbero usare [XFS](https://en.wikipedia.org/wiki/XFS) o [Btrfs](https://en.wikipedia.org/wiki/Btrfs) però sono stati riscontrati alcuni problemi con Btrfs.
Nessun altro filesystem dovrebbe essere utilizzato per le partizioni di installazione.

## Avvio da USB 

Si può avviare questa release da un'unità di memoria USB. Per trasferire l'immagine potresti:

### - Usare ROSA Image Writer disponibile nei nostri repository

Per installarlo utilizzare il seguente comando:

`sudo dnf --refresh install rosa-imagewriter`

Oppure, se non hai ancora OpenMandriva Lx, puoi trovare i link per il download di ROSA Image Writer a [questa pagina](http://wiki.rosalab.ru/en/index.php/ROSA_ImageWriter)
La capacità minima consigliata è di 4 GB. La memoria persistente non è necessaria.
Si noti che ciò **cancellerà** tutto il contenuto della vostra USB.

### > Per favore non utilizzare altri strumenti per la scrittura di USB come ad esempio alcuni tool di Windows (ad esempio Rufus) perchè troncano il nome del volume. Questo guasterebbe il processo di boot.
{.is-danger}

- Via dd

In alternativa puoi scrivere l'immagine nella tua USB usando dd:
`$ sudo dd if=<iso_name> of=<usb_drive> bs=4M`

Sostituisci `<iso_name>` con il percorso per l'ISO e `<usb_drive>` con la partizione del dispositivo USB, ad esempio `/dev/sdb`.

## SUSE Studio ImageWriter è stato testato e funziona per scrivere le immagini ISO su unità di memoria USB.

Avvio da file ISO
Grub2 entry da aggiungere in `/boot/grub2/grub.cfg`

## ```
submenu "OpenMandriva (64 bit)" {
        set isofile=/home/user/OpenMandrivaLx.4.1-plasma.x86_64.iso
        set isoname=OpenMandrivaLx_4.1
        loopback loop $isofile

        menuentry "OpenMandriva" {
                linux (loop)/boot/vmlinuz0 root=live:LABEL=${isoname} iso-scan/filename=${isofile} rd.live.image toram --
                initrd (loop)/boot/liveinitrd.img
        }
}
```

A proposito dei repository

Adesso abbiamo [om-repo-picker](/en/doc/repositories-tldr) aka Software Repository Selector per selezionare repository aggiuntive per avere una più ampia varietà di pacchetti disponibili.

## Non mischiare le repositories da release versioni o canali di aggiornamento diversi. Per esempio **non usare le repository Cooker su un sistema Rock**. Se usi Rock usa solo le repository Rock.
Ciò è spiegato nel dettaglio in [OpenMandriva Release Plan and Repositories](/en/doc/release-plan-and-repositories). 
Se mischi relese/repositories per i canali di aggiornamento e guasti il sistema l'unica soluzione sarà di reinstallare il sistema operativo da zero. Dopo aver reinstallato, non commettere più lo stesso errore.

Repository di OpenMandriva e disponibilità di software

Il sistema OMLx quando installato ha la repository `main` abilitata di default.

Ci sono anche repository supplementari chiamate `unsupported`, `restricted` e `non-free`.
Per avere la massima disponibilità di software gli utenti dovranno abilitare queste repo.
Trovi la spiegazione dei differenti repository [qui](/en/doc/release-plan-and-repositories)

## Gli utenti possono usare l'utility grafica Software Repository Selector per selezionare e deselezionare ciò che desiderano utilizzare.

Nuove Features e Cambiamenti Importanti

In modo da tenere il passo con gli ultimi cambiamenti per quanto riguarda la sicurezza e la scrittura di codice informatico su Linux ci sono stati dei cambiamenti importanti in OMLx4.1.
- Cambiamenti Importanti:
- Il kernel è stato aggiornato alla versione 5.5.0
- Qt è stato aggiornato alla versione 5.14.1
- Plasma è stato aggiornato: Frameworks 5.66, Desktop Plasma 5.17.5, Applicazioni 19.12.1
- Zypper è stato introdotto come gestore di pacchetti alternativo

Sono disponibili altri desktop alternativi
- Applicazioni di brand-name OpenMandriva:
- Desktop Presets (om-feeling-like): Strumento per personalizzare l'aspetto del tuo desktop Plasma OpenMandriva in modo che tu possa renderlo più simile ad altri sistemi che sei abituato a utilizzare.

## Update Configuration (om-update-config): Strumento per configurare aggiornamenti automatici.
Aggiornamento da una versione precedente

Attualmente si consiglia una nuova installazione.
Se vuoi tentare comunque l'aggiornamento, assicurati di avere un backup di tutti i tuoi dati.


> Si prega di notare: Gli strumenti grafici come Discover e dnfdragora non aggiorneranno OMLx 4.0 a OMLx 4.1. **Se lo farai, il sistema si guasterà**.
{.is-danger}
Nessuno di questi gestori di pacchetti GUI è in grado di fare questo tipo di aggiornamento chiamato "aggiornamento della distribuzione".
E' necessario un `dnf --allowerasing disto-sync` non un `dnf upgrade`. Inoltre ci sono problemi di dipendenze che richiedono che venga digitato un comando unico da console come segue:

 ```
$ sudo dnf remove java-12-openjdk && sudo dnf --refresh --best --allowerasing distro-sync
```


# Più dettagli [qui](https://forum.openmandriva.org/t/3313)
Errata

# Vedi [4.1/Errata](/releases/omlx41/errata).
Aiuta il progetto

![om-donate.svg](/images/om-donate.svg){.align-left}I team di sviluppo di OpenMandriva (Cooker & QA) cercano sempre nuovi contributori che assistano nella creazione e nel mantenimento di pacchetti e per assistere nella correzione dei bug e nel testing. Sei il benvenuto se vuoi entrare e aiutarci in questo lavoro che non è solo soddisfacente ma è anche tremendamente divertente!

I team di sviluppo di OpenMandriva (Cooker & QA) cercano sempre nuovi contributori che assistano nella creazione e nel mantenimento di pacchetti e per assistere nella correzione dei bug e nel testing. Sei il benvenuto se vuoi entrare e aiutarci in questo lavoro che non è solo soddisfacente ma è anche tremendamente divertente!
