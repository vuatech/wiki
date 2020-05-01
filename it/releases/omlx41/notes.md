---
title: OpenMandriva Lx 4.1 Note di rilascio
description: 
published: true
date: 2020-05-01T14:56:41.443Z
tags: 4.1
---

# OpenMandriva Lx 4.1 Note di rilascio
Il Team di OpenMandriva Lx è lieto di annunciare la disponibilità di **OpenMandriva Lx 4.1**. [Codename](/en/releases/codename) Mercury

## Available Media

This release is available as a live media DVD or USB flash drive (memory stick), downloadable in ISO format. These are available on our [downloads page](https://www.openmandriva.org/en/download). USB flash drive installation is usually noticeably faster. As always speed depends on many factors.
*Live media* means you are able to run OpenMandriva Lx straight from a DVD or memory stick (see below) and try it before installing it. You may also install the system to hard disk either from the running live image or from the boot manager.

Available ISO files are:
- [KDE Plasma](https://www.kde.org/plasma-desktop) desktop only full featured (includes the most common used functionalities, multimedia and office software).
- znver1 Plasma: we have also built a version specifically for current AMD processors (Ryzen, ThreadRipper, EPYC) that outperforms the generic (x86_64) version by taking advantage of new features in those processors.
znver1 è disponibile solamente per i seguenti processori (Ryzen, Thread Ripper, EPYC), non installare su nessun altro tipo di hardware.

## Raccomandazioni per l'Hardware

OpenMandriva Lx4.1 richiede un minimo di 2.0 GB di memoria e almeno 10 GB di spazio su disco fisso (guarda sotto per problemi di partizionamento già rilevati).

> Nota importante: Hardware Grafico:
> Il desktop KDE Plasma richiede una scheda grafica che supporti OpenGL 2.0 o superiore.
> Raccomandiamo di utilizzare schede grafiche  AMD, Intel, Adreno o VC4.
{.is-warning}


## Connessione Internet

L'installer Calamares controlla se c'è una connessione internet disponibile, ma OpenMandriva Lx 4 verrà installato senza problemi anche se la connessione non è disponibile. Installare semplicemente come faresti normalmente e procedere ad utilizzare il sistema normalmente è perfettamente OK.
Aggiornare un sistema del genere richiederà di essere temporaneamente connessi a Internet oppure si possono scaricare i pacchetti in un altro sistema e trasferirli al sistema installato e procedere a installare i pacchetti aggiornati.
Ma fino a che non  si è connessi a Internet si può semplicemente usare il sistema senza aggiornarlo per quanto vogliamo.

## Macchine Virtuali
Per ora l'unico software di virtualizzazione su cui le ISO di OMLx sono state testate è VirtualBox. I requisiti hardware sono gli stessi anche quando si sta usando una macchina virtuale.
Per quanto riguarda VirtualBox bisogna che tu abbia a disposizione un minimo di 2048 MB di memoria altrimenti OpenMandriva fallirà il processo di boot.
Ancora per quanto riguarda VirtualBox è consigliato installare in una macchina virtuale nuova, perchè provare a installare il sistema in una già esistente potrebbe occasinalmente non funzionare.

## Installer Calamares

Calamares è un installer strutturale.
Da design è molto personalizzabile in modo da soddisfare un'ampia varietà di casi e bisogni. L'obiettivo di questo installer è essere facile da usare, bello, pragmatico, inclusivo e indipendente dalla distribuzione.
Calamares include un'opzione per il partizionamento avanzato, che supporta sia operazioni di partizionaamento manuale sia operazioni di partizionamento automatizzato.
Questo è il primo installer con un'opzione automatizzata "Rimpiazza Partizione", che rende semplice il riutilizzo di una partizione per necessità di distribution testing.
Tante distribuzioni Linux usano Calamares come installer e ciascuna ha la sua implementazione e i suoi standard. Il fatto che qualcosa nell'installer di OpenMandriva non si conforma all'esperienza dell'utente con altre distribuzioni Linux non significa che quel qualcosa sia un bug.

## Partizionamento

Per ora il partizionamento LVM e i setup Raid con l'installer Calamares non sono supportati. **Ciò si applica a tutti i partizionamenti**, tutte le installazioni su hardware: Se si possiede un computer con sistema UEFI/EFI e il tuo BIOS offre una scelta nel momento di boot ad esempio:

`Chiavetta USB`
`Chiavetta USB UEFI`
or 
`supporto DVD`
`supporto DVD UEFI`

In questi casi devi avviare scegliendo l'opzione UEFI. Ma sappi che non tutti i computer fanno ciò. Alcuni con BIOS più spartane offriranno solo un opzione e quasi sempre sarà quella corretta. Quindi per esempio se su un notebook non vedi le possibilità scritte sopra non preoccuparti. Se hai unità di memoria multiple ciò che devi fare è avere lo stesso tipo di tabelle di partizionamento. Devono essere o tutte gpt o tutte mbr per fare si che tutto funzioni correttamente.
Su sistemi UEFI in situazioni di multi-boot con unità di memoria multiple se si ha già una partizione `/boot/efi` esistente bisogna usare quella. Il partizionatore non creerà un'altra partizione `/boot/efi` con flag appropriate e quindi l'installazione risulterà in un errore di bootloader non installato. Non formattare bisogna solo settare il mount point a `/boot/efi`. Uno può avere tanti bootloader per sistemi operativi diversi nella stessa partizione `/boot/efi`. Se c'è bisogno di cambiare bootloader, ciò si fa nelle impostazioni del BIOS.

## NVME SSDs

Alcune SSD NVME potrebbero non essere riconosciute dalla live ISO di OMLx4.1.
La *Live* ISO ha 2 stratagemmi per ciò sotto "Troubleshooting" nel Menù di Grub 2. Sono `(PCIE ASPM=OFF)` and `(NVME APST=OFF)`. Speriamo che ciò funzioni per l'hardware della maggior parte delle persone. Il problema è conosciuto e gli sviluppatori di OMLx4 ci stanno lavorando su. Vedi di più in 4.1/Errata.
La release di OMLx4.1 include kernel 5.5.0 e riconoscimento hardware per SSD NVME dovrebbe essere considerevolmente migliorato. Si sa che alcune SSD NVME che nella versione precedente non erano riconosciute ora lo sono con questa versione del kernel. Questo problema è molto specifico per alcuni tipi di hardware particolare.

## Installer e Supporto EFI

Questa release di OpenMandriva Lx supporta il boot e l'installazione con e senza  [UEFI](https://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface).
Si noti che il secure boot NON è supportato.
Se si desidera effettuare un installazione EFI su un disco MBR già esistenete sarà necessario convertire la tabella delle partizioni presente sul disco usando lo schema di partizionamento GPT. Per fare ciò è necessario utilizzare il programma gdisk. Una tipica invocazione potrebbe essere gdisk `gdisk /dev/sda` : la partizione esistente verrà convertita in schema GPT in memoria.Attenzione che facendo ciò potrebbe verificarsi una perdita di dati, il disco non sarà alterato fino a che la tabella delle partizioni viene scritta prmendo <kbd>w</kbd>. Consigliamo di effettuare un backup dei tuoi dati importanti prima di procedere con questo tipo di operazioni.
Ci potrebberoi essere occasioni nelle quali la conversione non può essere effettuata, questo è solitamente dovuto a spazio insufficiente per scrivere la tabella delle partizioni all'inizio o alla fine del disco. Potrebbe essere necessario eliminare oppure ridimensionare una partizione per fare spazio, gparted è il tuo migliore amico in queste circostanze.
C'è ancora il bisogno di creare una partizione efi per contenere l'equipaggiamento di boot, questa partizione va creata mentre si usa  l'installer Calamares. Quando l'installer raggiunge il momento del partizionamento la partizione di root (/) dovrebbe essere rimossa e una piccola partizione da 330MB in FAT32 o FAT16 deve essere creata all'inizio del disco. Se lo spazio su disco è critico si può usare una partizione più piccola ma bisogna assicurarsi che sia settata come FAT16 o FAT32 in Calamares altrimenti l'installazione non andrà a buon fine.
Se non seguirai queste indicazioni l'installazione del boot loader fallirà. Successivamente partiziona il disco in maniera normale.
Per favore condividete le vostre esperienze nei forum così che noi abbiamo modo di migliorare questo aspetto dell'installazione.
Se stai installando in dual booting con Windows 8, 8.1, 10 o altri sistemi operativi EFI, come precauzione per favore assicurati di avere dischi di recupero e di avere un backup dei tuoi dati importanti. 
Il nostro testing è stato limitato a questa configurazione, ma sono stata effettuate installazioni con successo senza problemi.
Ogni tipo di feedback che riguarda quest'area è bene accetto.

## Cambiare tipo di partizione 

Per favore si noti che Calamares non può convertire da un tipo di partizione a un'altra e conservare i dati delle partizioni.
Se fai partire Calamares in Live non è possibile cambiare il tipo di partizione di una partizione esistente. Provare a eseguire questa operazione genererà un messaggio di errore.
In modo da fare ciò bisgna prima eliminare la partizione e crearne una nuova con il tipo di partizione desiderato.

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

Oppure, se non hai ancora OpenMandriva Lx, puoi ottenere i link di download per ROSA Image Writer a [questa pagina](http://wiki.rosalab.ru/en/index.php/ROSA_ImageWriter)
La capacità minima consigliata è di 4 GB. La memoria persistente non è necessaria.
Si noti che ciò **cancellerà** tutto il contenuto della vostra USB.

> Per favore non utilizzare altri strumenti per la scrittura di USB come ad esempio alcuni tool di Windows (ad esempio Rufus) perchè troncano il nome del volume. Questo guasterebbe il processo di boot.
{.is-danger}

### - Via dd

In alternativa puoi scrivere l'immagine nella tua USB usando dd:
`$ sudo dd if=<iso_name> of=<usb_drive> bs=4M`

Sostituisci `<iso_name>` con il percorso per l'ISO e `<usb_drive>` con la partizione del dispositivo USB, ad esempio `/dev/sdb`.

SUSE Studio ImageWriter è stato testato e funziona per bruciare le ISO su unità di memoria USB.

## Avvio da file ISO

Grub2 entry da aggiungere in `/boot/grub2/grub.cfg`
```
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

## A proposito dei repository

Adesso abbiamo [om-repo-picker](/en/doc/repositories-tldr) aka Software Repository Selector per selezionare repository aggiuntive per avere una più ampia varietà di pacchetti disponibili.

Non mischiare le repositories da release versioni o canali di aggiornamento diversi. Per esempio **non usare le repository Cooker su un sistema Rock**. Se usi Rock usa solo le repository Rock.
Ciò è spiegato nel dettaglio in [OpenMandriva Release Plan and Repositories](/en/doc/release-plan-and-repositories). 
Se mischi relese/repositories per i canali di aggiornamento e guasti il sistema la soluzione è reinstallare il sistema operativo da zero. E dopo aver reinstallato tutto non farlo più.

## Repository di OpenMandriva e disponibilità di software

Il sistema OMLx quando installato ha la repository main abilitata di default.

Ci sono anche repository chiamate `unsupported`, `restricted` e `non-free`.
Per avere la massima disponibilità di software gli utenti dovranno abilitare queste repo.
Le varie repo sono spiegate [qui](/doc/release-plan-and-repositories)

Gli utenti possono usare l'utility grafica Software Repository Selector per selezionare e deselezionare ciò che desiderano utilizzare.

## Nuove Features e Cambiamenti Importanti

In modo da tenere il passo con gli ultimi cambiamenti per quanto riguarda la sicurezza e la scrittura di codice informatico su Linux ci sono stati dei cambiamenti importanti in OMLx4.1.

Cambiamenti Importanti:
- Il kernel è stato aggiornato alla versione 5.5.0
- Qt è stato aggiornato alla versione 5.14.1
- Plasma è stato aggiornato: Frameworks 5.66, Desktop Plasma 5.17.5, Applicazioni 19.12.1
- Zypper è stato introdotto come gestore di pacchetti alternativo
- Sono disponibili altri desktop alternativi

Applicazioni di brand-name OpenMandriva:
- Desktop Presets (om-feeling-like): Strumento per personalizzare l'aspetto del tuo desktop Plasma OpenMandriva in modo che tu possa renderlo più simile ad altri sistemi che sei abituato a utilizzare.
- Update Configuration (om-update-config): Strumento per configurare aggiornamenti automatici.

# Errata
Vedi [4.1/Errata](/releases/omlx41/errata).

# Aiuta il progetto
![om-donate.svg](/images/om-donate.svg){.align-left}I team di sviluppo di OpenMandriva (Cooker & QA) cercano sempre nuovi contributori che assistano nella creazione e nel mantenimento di pacchetti e per assistere nella correzione dei bug e nel testing. Sei il benvenuto se vuoi entrare e aiutarci in questo lavoro che non è solo soddisfacente ma è anche tremendamente divertente!

I team di sviluppo di OpenMandriva (Cooker & QA) cercano sempre nuovi contributori che assistano nella creazione e nel mantenimento di pacchetti e per assistere nella correzione dei bug e nel testing. Sei il benvenuto se vuoi entrare e aiutarci in questo lavoro che non è solo soddisfacente ma è anche tremendamente divertente!

Se senti che il tuo talento non risiede nel campo del software, allora il gruppo Workshop, che è composto dai Team Artwork, Documentazione, Traduzione, e Comunicazione, è sempre aperto per il ricevimento di lavori artistici e traduzioni. I nuovi contributori che desiderano aiutare con questi compiti ad ampio raggio dovrebbero visitare la wiki per ricevere più dettagli e imparare come entrare! In via alternativa puoi usare il nostro [Forum](http://forum.openmandriva.org/).

Inoltre mantenere i nostri server online e funzionanti costa tempo e denaro. Se puoi, per favore dona per tenere le luci accese.
