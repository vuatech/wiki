---
title: Guida specifica allo stile della wiki di OpenMandriva
description: 
published: true
date: 2020-04-22T16:52:59.603Z
tags: documentation, policies, wiki, howto
---

# Guida specifica allo stile della wiki di OpenMandriva
> Prima leggi [Guida generale allo stile del wiki](/doc/wiki-style-guide)
{.is-danger}

## Regole specifiche della wiki di OpenMandriva

> Questa pagina non è definitiva (lavori in corso), ma sarà aggiornata nel tempo non appena troverò motivo di aggiungere altre istruzioni.
{.is-info}


### Immagini
Gli screenshot e le comuni immagini che vengono inserite nelle pagine della wiki devono essere caricate **soltanto** nella cartella `/images`.
E' il motivo per cui la cartella è stata creata.

I nomi dei file immagine non devono contenere:
- Spazi (utilizza un trattino al loro posto)
- Trattini bassi (usa un trattino normale al loro posto)
- Punti (sono riservati alle estensioni dei file)
- Caratteri URL non sicuri (come segni di punteggiatura, virgolette, simboli matematici, ecc...)

Quando è possibile, rinomina i tuoi file immagine con qualcosa che abbia un significato relativo alla pagina o a ciò che l'immagine mostra.

### Percorsi (paths)
I percorsi devono essere in lettere minuscole. Usa i trattini per separare le parole.
Non sono ammessi segni di punteggiatura ad eccezione di trattini e/o trattini bassi.
-- Nota: anche se *tecnicamente* permesso, lo standard della wiki di OpenMandriva usa i trattini normali e non quelli bassi.
Non è necessario nominare il percorso con l'intero titolo della pagina: si può, anzi si dovrebbe quando è possibile, essere accorciato.

I percorsi non possono contenere i seguenti caratteri:
- Spazi (utilizza un trattino al loro posto)
- Punti (sono riservati alle estensioni dei file)
- Caratteri URL non sicuri (come segni di punteggiatura, virgolette, simboli matematici, ecc...)

Siccome spesso dobbiamo scrivere il numero di versione della release (4.0, 4.1, 4.2, ecc...), al momento della creazione delle nuove pagine semplicemente converti in  `40`, `41`, `42`, ecc. omettendo il punto nel percorso.

Se la pagina è chiamata "*How to foo bar whatever*" il percorso deve essere `/doc/guides/howto-something`
Non `how-to`, né `howtos`, né `how-tos`, ecc.

### Flusso di lavoro delle traduzioni
Per la migliore organizzazione mantieni il percorso originale inglese senza modificarlo, cambia solo il prefisso della lingua. Di conseguenza `en/home` diventerà `fr/home`, `it/home`, ecc.
Come altro esempio `/en/doc/guides/howto-list-packages-iso` diventerà `/it/doc/guides/howto-list-packages-iso` e **il titolo** della tua pagina tradotta (che è tutt'altra cosa rispetto al percorso) sarà "*Come ottenere una lista di tutti i pacchetti presenti nella ISO*"
Tieni a mente che il percorso è una convenzione, il titolo della pagina può essere qualsiasi cosa nella tua lingua.
L'azione di cui sopra è comunque semplificata e viene eseguita automaticamente cliccando sull'icona *Language* <i class="v-icon mdi mdi-web"></i> in alto a destra della pagina.

\-






