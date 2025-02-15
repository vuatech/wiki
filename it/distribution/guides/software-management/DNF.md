---
title: Usare dnf in OpenMandriva Lx
description: 
published: true
date: 2025-02-15T11:00:42.718Z
tags: documentation, dnf, user-guide
editor: markdown
dateCreated: 2020-03-06T18:48:34.373Z
---

# Usare dnf in OpenMandriva Lx

> Per la documentazione completa e più comandi vedere [DNF Command Reference](https://dnf.readthedocs.io/en/latest/command_ref.html)
{.is-success}


## Alcuni comandi di base

- Installa un pacchetto:
`$ sudo dnf --refresh install <package_name>`

- Rimuovi un pacchetto:
`$ sudo dnf remove <package_name>`

- Cerca repository per un pacchetto:
`$ sudo dnf search <package_name>`
Nota: 'dnf search' funzionerà anche con nomi parziali

- Pulisce ogni file e pacchetto rimasto nella cache e rimuove i metadata della repository:
`$ sudo dnf clean all ; dnf clean all`

- Aggiorna il tuo sistema Rock:
`$ sudo dnf --refresh upgrade `

- Aggiorna il tuo sistema ROME (rolling):
`$ sudo dnf --refresh distro-sync `

## Altri comandi dnf molto comuni

`autoremove`
Rimuove pacchetti installati come dipendenze che non sono più richieste dai programmi installati nel sistema.
> Stai attento quando usi `dnf autoremove`. E' possibile che questo comando rimuova qualcosa che non vuoi sia rimosso. E' una buona norma tenere una lista dei pacchetti che sono stati rimossi automaticmente in modo che tu sappia cosa reinstallare se ciò dovesse accadere.
Nota: Puoi trovare i pacchetti autorimossi in `/var/log/dnf.log`
{.is-warning}


`check-update`
Controlla la disponibilità di aggiornamenti, ma non li scarica né tantomeno li installa

`downgrade`
Riporta il pacchetto selezionato alla versione precedente

`info`
Mostra informazioni base riguardanti un pacchetto tra cui nome, versione, release e descrizione

`reinstall`
Reinstalla un pacchetto attualmente già installato

`repolist`
Mostra una lista dei repository attivi

## Alcuni comandi possono essere abbreviati

`dnf in=dnf install`
`dnf ri=dnf reinstall`
`dnf dg=dnf downgrade`
`dnf rm=dnf remove`
`dnf up=dnf upgrade`
`dnf dsync=dnf distro-sync`

## Alcune opzioni comuni di dnf

`--allowerasing`
Abilita la cancellazione di pacchetti installati per risolvere dipendenze. Questa opzione può essere usata in alternativa al comando yum swap nel quale i pacchetti da rimuovere non sono esplicitamente definiti. Usa questa opzione con attenzione, se la usi devi sapere ciò che stai facendo altrimenti rischi di rompere il sistema

`-b, --best`
Prova le migliori versioni disponibili dei pacchetti nella transazione. In maniera specifica durante dnf upgrade che per default salta gli aggiornamenti che non possono essere installati per problemi di dipendenze, lo switch forza dnf a considerare solo gli ultimi pacchetti. Nel momento in cui ci si imbatte in pacchetti con dipendenze rotte, dnf fallirà fornendo un motivo perchè l'ultima versione non può essere installata

`--disable, --set-disabled`
Disabilita repository specificati (salva automaticamente). L'opzione deve essere usata assieme al comando config-manager (dnf-plugins-core)

`--disablerepo=<repoid>`
Disabilita specifici repository attraverso un id o un glob. Questa opzione è mutualmente esclusiva con `--repo`

`--downloadonly`
Scarica i pacchetti risolti senza effettuare nessuna transazione (install/upgrade/erase)

`--enable, --set-enabled`
Abilita repository specificati (salva automaticamente). L'opzione deve essere usata assieme al comando config-manager (dnf-plugins-core)

`--enablerepo=<repoid>`
Abilita repository addizionali attraverso un id o un glob

`--exclude=<package_name>`
Esclude alcuni pacchetti dalla transazione

`--nobest`
Imposta l'opzione best a Falso, in modo che le transazioni non siano limitate esclusivamente ai migliori candidati

`-y, --assumeyes`
Risponde si a tutte le domande automaticamente

## Di più
`$ dnf --help`
e
`$ man dnf4` o `$ man dnf5` 

Per leggere il menù di help ci vogliono 1 minuto, 1 minuto e mezzo. Per leggere la pagina del manuale di dnf ci vogliono dai 3 ai 5 minuti.
Entrambi sono progettate per essere disponibili alla consultazione degli utenti nel caso debbano trovare velocemente il modo di fare qualcosa mentre stanno usando il loro sistema.

Esistono anche altre wiki e documentazioni riguardanti dnf: [Using the DNF software package manager](https://docs.fedoraproject.org/en-US/quick-docs/dnf/), [Fedora wiki page](https://fedoraproject.org/wiki/DNF?rd=Dnf), and [DNF Command Reference](https://dnf.readthedocs.io/en/latest/command_ref.html).


