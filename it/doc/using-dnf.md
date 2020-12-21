---
title: Usare dnf in OpenMandriva Lx
description: 
published: true
date: 2020-04-27T12:06:14.071Z
tags: documentation, dnf, user-guide
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

- Pulisci ogni file e pacchetto rimasto nella cache per rimuovere i metadata della repository:
`$ sudo dnf clean all ; dnf clean all`

- Aggiorna il tuo sistema:
`$ sudo dnf --refresh upgrade `

## Altri comandi dnf molto comuni

`autoremove`
Rimuove pacchetti installati come dipendenze che non sono più richieste dai programmi installati nel sistema.
> Stai attento quando usi dnf autoremove. E' possibile che questo comando rimuova qualcosa che non vuoi sia rimosso. E' una buona idea tenere una lista dei pacchetti che sono stati "autorimossi" in modo che tu sappia cosa reinstallare se ciò succede.
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
Mostra una lista delle repository attivate

## Alcune opzioni comuni di dnf

`--allowerasing`
Abilita la cancellazione di pacchetti installati per risolvere dipendenze. Questa opzione può essere usata in alternativa al comando yum swap nel quale i pacchetti da rimuovere non sono esplicitamente definiti. Usare questa opzione con attenzione, se la usi devi sapere ciò che stai facendo altrimenti rischi di rompere il sistema

`-b, --best`
Prova le migliori versioni disponibili dei pacchetti in transizione. In maniera specifica durante dnf upgrade che per default salta gli aggiornamenti che non possono essere installati per problemi di dipendenze, lo switch forza dnf a cconsiderare solo gli ultimi pacchetti. Nel momento in cui ci si imbatte in pacchetti con dipendenze rotte, dnf fallirà nel dare una ragione sul perchè l'ultima versione non può essere installata

`--disable, --set-disabled`
Disabilita repository specificate (salva automaticamente). L'opzione deve essere usata insieme al comando di configurazione di gestione (dnf-plugins-core

`--disablerepo=<repoid>`
Disabilita specifiche repository attraverso un id o un glob. Questa opzione è mutualmente esclusiva con `--repo`.

`--downloadonly`
Scarica i pacchetti risolti senza effettuare nessuna transazione rpm (install/upgrade/erase)

`--enable, --set-enabled`
Abilita repository specificate (salva automaticamente). L'opzione deve essere usata assieme al comando di config-manager (dnf-plugins-core)

`--enablerepo=<repoid>`
Abilita repository addizionali attraverso un id o un glob

`--exclude=<package_name>`
Esclude alcuni pacchetti dalla transazione

`--nobest`
Imposta la migliore opzione come Falso, in modo che le transazioni non siano limitate esclusivamente ai migliori candidati

`-y, --assumeyes`
Risponde si a tutte le domande automaticamente

## Di più
`$ dnf --help`
e
`$ man dnf`

Per leggere il menù di help ci vogliono 1 minuto, 1 minuto e mezzo. Per leggere la pagina del manuale di dnf ci vogliono dai 3 ai 5 minuti.
Entrambe sono progettate per essere disponibili agli utenti per essere consultate nel caso gli utenti debbano trovare velocemente il modo di fare qualcosa mentre stanno usando il loro sistema.

Ci sono anche altre wiki e documentazioni riguardanti dnf: [Using the DNF software package manager](https://docs.fedoraproject.org/en-US/quick-docs/dnf/), [Fedora wiki page](https://fedoraproject.org/wiki/DNF?rd=Dnf), and [DNF Command Reference](https://dnf.readthedocs.io/en/latest/command_ref.html).


