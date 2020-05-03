---
title: OpenMandriva Lx 4.1 Errata
description: 
published: true
date: 2020-05-03T07:26:35.867Z
tags: 4.1
---

# OpenMandriva Lx 4.1 Errata -  Problemi Conosciuti

> Come in ogni release, ci sono problemi e bug che non sono ancora stati risolti. Questa pagina documenta quelli che potrebbero causare inconvenienze e dove possibile dettaglia come si potrebbero risolvere.
{.is-info}


**Si raccomanda di leggere le ultime** [Note di Rilascio](/releases/omlx41/notes) **sulla nostra wiki**.

## Schede Grafiche NVIDIA
Questa release include i driver inversamente ingenierizzati nouveau, che danno un buon supporto per la maggior parte delle schede grafiche NVIDIA. Per qualche necessità di dual screen sono migliori dei driver binari di NVIDIA perchè supportano la rotazione dello schermo su un secondo monitor, ciò è molto utile per i monitor con schermi rotabili.
Alcuni utenti potrebbero usare i driver dal sito web di NVIDIA , ma questi ultimi non possono essere supportati da OpenMandriva per molteplici ragioni.
Installare e mantenere un qualsiasi driver proprietario NVIDIA è esclusivamente un'opzione e una responsabilità scelta dall'utente.

## NVME SSDs
C'è un problema ben conosciuto con alcune (specialmente quelle nuove) SSD NMVE e apparecchi PCIE dove le SSD potrebbero non venir riconosciute. Per la nostra Live ISO c'è una soluzione descritta nelle [Note di Rilascio](/releases/omlx41/notes).
Il problema è conosciuto e gli sviluppatori di OpenMandriva ci stanno lavorando assieme agli sviluppatori upstream.
La release di OMLx 4.1 include kernel 5.5.0 e il riconoscimento hardware per le SSD NVME dovrebbe essere considerevolmente migliorato.
Si sa che alcune SSD NVME Samsung che prima non venivano riconosciute ora sono inserite in questa versione del kernel. Questo problema ovviamente è strettamente legato all'hardware dell'utente.

Come workaround in un sistema installato si consiglia di aggiungere una delle seguenti stringhe in `/etc/default/grub` e lanciare il comando `update-grub2` per fare si che la soluzione sia globale.
Dovresti usare quella che sai abbia funzionato in modalità *Live* ISO.

Se `(PCIE ASPM=OFF)` ha funzionato per te aggiungi:
`pcie=aspm=off`
alle linee
`GRUB_DECLINE_LINUX_DEFAULT`
`GRUB_DECLINE_LINUX_RECOVERY`
in 
`/etc/default/grub` 
e dunque fai partire il comando:
`$ sudo update-grub2`

Se `(NVME APST=OFF)` ha funzionato aggiungi invece:
`nvme_core.default_ps_max_latency_us=0`

Come sempre, gli utenti sono incoraggiati a fare domande su qualsiasi argomento non capiscano sul nostro [forum](https://forum.openmandriva.org/).

## GEOIP
L'opzione automatica GEOIP dell'installer potrebbe non impostare correttamente il tuo fuso orario.

## Come configurare la stampante
Accendi la tua stampante e osserva se viene configurata automaticamente. Fai attenzione che i driver corretti siano installati. Se la stampante è stata autoconfigurata e hai i driver giusti bene, sei a posto.
Altrimenti, spegni la stampante. Apri *Printer Settings* aka `system-config-printer` e rimuovi la tua stampante.
Se i driver corretti non sono stati installati automaticamente devi aggiungere un pacchetto software.

Il prossimo passo è capire qual è il pacchetto da installare.

In OpenMandriva Lx è molto probabile che sia un pacchetto `task-printing` specifico per la marca della tua stampante. I pacchetti sono:
- task-printing-canon
- task-printing-epson
- task-printing-hp
- task-printing-lexmark
- task-printing-okidata
- task-printing-misc

Installa il pacchetto che coincide con la marca della tua stampante o il pacchetto misc se non è nella lista. Esempio usando okidata:
```
$ sudo dnf install task-printing-okidata
```
Ora accendi la tua stampante e dovrebbe configurasi in automatico (potrebbe essere necessario un reboot).

Se non funziona, chiedi aiuto [qui](https://forum.openmandriva.org/c/en/support)

## Discover
Riguardo al software nei repository, Discover potrebbe non mostrare tutti i pacchetti disponibili.
Ciò è dovuto al fatto che la sua cache non è stata ripulita e le liste dei repository non sono state scaricate al primo avvio.
Per risolvere il problema usa i seguenti comandi:
```
$ sudo rm -rf /var/cache/PackageKit/* /var/cache/app-info/*
$ sudo pkcon refresh force
```
Se vuoi esplorare i repository aggiuntivi li devi attivare usando il Selettore di repository [Software Repository Selector](/en/doc/repositories-tldr) e aggiornare nuovamente la cache.

## Multiboot
Nel 'mondo reale' il multiboot funziona bene il più delle volte ma in caso di problemi si ricorre ad un espediente più che un fix vero e proprio.
Queste sono semplicemente le realtà del multiboot.

Inoltre non è attualmente possibile per il Team QA di OpenMandriva testare il nostro bootloader con ogni filesystem su ogni distribuzione Linux, o neppure sulle migliori 10 distribuzioni Linux. Il fatto è che per il multiboot con Windows o altre distribuzioni ci affidiamo esclusivamente ai report che i nostri utenti ci mandano per capire cosa funziona e cosa non funziona quando si ha a che fare con il multibooting.

Un problema conosciuto riscontrato con il bootloader di OM Lx è che grub2 non crea voci di boot per sistemi OpenSUSE che utilizzano il filesystem btrfs. Funziona correttamente invece con sistemi OpenSUSE che utilizzano il filesystem ext4.
Ciò è dovuto al fatto che openSUSE usa una sintassi personalizzata nelle loro patch che non sono compatibili con il codice di OpenMandriva Lx. Non è attualmente risaputo se il bootloader di OM Lx funzioni o no con un sistema OpenSUSE che utilizzi un qualsiasi altro filesystem ad esempio XFS o F2FS.

L'espediente per gli utenti è di cambiare bootloader nelle impostazioni firmware del BIOS o UEFI.
Un'alternativa può essere quella di usare il bootloader di OpenSUSE se quest'ultimo riconosce il tuo sistema OpenMandriva.
Finchè i nostri utenti riferiscono problemi con il multiboot noi aggiusteremo quello che possiamo. I problemi che non siamo in grado di risolvere verrano riportati nei documenti Errata delle nostre release.

