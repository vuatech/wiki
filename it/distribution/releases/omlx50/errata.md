---
title: OpenMandriva Lx 5.0 Errata
description: 
published: true
date: 2025-02-12T09:23:38.329Z
tags: 5.0
editor: markdown
dateCreated: 2022-12-26T17:59:33.144Z
---

# OpenMandriva Lx 5.0 Errata - Problemi conosciuti

> Come in ogni release, ci sono problemi e bug che potrebbero non essere stati ancora risolti. Questa pagina documenta ciò che può causare inconvenienti e, ove possibile, spiega come risolvere.
{.is-info}

**Si prega di leggere anche [5.0/Release Notes](/distribution/releases/omlx50/notes)**.
<br />

## Problemi conosciuti e workaround
<br />

### Schede grafiche NVIDIA
Questa versione include il driver nouveau, che offre un discreto supporto alla maggior parte delle schede nvidia.
In caso di doppio schermo in realtà è migliore del driver nvidia, in quanto supporta la rotazione dello schermo su un secondo monitor, utile per i monitor con schermi ruotabili.
Gli utenti possono usare i driver dal sito web di nvidia, ma OpenMandriva non è in grado di supportarli per una serie di motivi.
L'installazione e la manutenzione di qualsiasi driver proprietario nvidia è di esclusiva competenza e responsabilità dell'utente. 
Esistono driver nvidia supportati dalla comunità e disponibili nei repository non-free.
<br />

### NVME SSDs
Esiste un problema ben noto con alcune unità SSD NVME (soprattutto quelle più recenti) e dispositivi PCIE in cui l'unità SSD potrebbe non essere riconosciuta.
Il problema è conosciuto e in fase di elaborazione da parte degli sviluppatori di OpenMandriva e degli sviluppatori upstream.

![header-tr-50.svg](/assets/header-tr-50.svg){.align-abstopright}
