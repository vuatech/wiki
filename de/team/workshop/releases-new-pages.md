---
title: Dokumentation zur Erstellung von Release-Seiten
description: 
published: true
date: 2021-09-26T21:47:46.114Z
tags: Dokumentation, Wiki
editor: Markdown
dateCreated: 2020-03-07T18:55:42.072Z
---

# Dokumentation zur Erstellung von Release-Seiten

Für jedes neues Release, das erstellt werden soll:

## Finales Release (GA)

### Hauptseite 'Übersicht'

Pfadmuster:
`/releases/omlxNN`
example: /releases/omlx42

### Unterseiten
#### Was ist neu?
Pfadmuster:
`/releases/omlxNN/new`
example: /releases/omlx42/new

#### 'Anmerkungen'
Pfadmuster:
`/releases/omlxNN/notes`
example: /releases/omlx42/notes

#### 'Errata' 
Pfadmuster:
`/releases/omlxNN/errata`
example: /releases/omlx42/errata

## Development-Releases (Alpha, Beta, RC)

### Unterseiten
Pfadmuster:
`/releases/omlxNN/alpha`
`/releases/omlxNN/beta`
`/releases/omlxNN/rc`

`/releases/omlxNN/alpha/notes`
`/releases/omlxNN/beta/notes`
`/releases/omlxNN/rc/notes`

`/releases/omlxNN/alpha/errata`
`/releases/omlxNN/beta/errata`
`/releases/omlxNN/rc/errata`

Beispiel: /releases/omlx42/alpha
Beispiel: /releases/omlx42/beta
Beispiel: /releases/omlx42/rc

Beispiel: /releases/omlx42/alpha/notes
Beispiel: /releases/omlx42/beta/notes
Beispiel: /releases/omlx42/rc/notes

Beispiel: /releases/omlx42/alpha/errata
Beispiel: /releases/omlx42/beta/errata
Beispiel: /releases/omlx42/rc/errata

## Addendum - Pfade
Pfade müssen klein geschrieben werden. Verwenden Sie gestrichelt, um die Wörter zu trennen.
Interpunktion ist nicht erlaubt, außer Gedankenstrichen/Hyphen und/oder Unterstrichen.

Pfade dürfen die folgenden Zeichen nicht enthalten:
- Leerzeichen (stattdessen Gedankenstriche verwenden)
- Punkt (reserviert für Dateierweiterungen)
- Unsichere URL-Zeichen (wie Interpunktionszeichen, Anführungszeichen, mathematische Symbole etc.)

Da wir oft Release-Versionsnummern (4.0, 4.1, 4.2 etc.) schreiben müssen, wandeln wir sie bei der Erstellung neuer Seiten einfach in `40`, `41`, `42` usw. um, indem wir den Punkt in dem Pfad weglassen.

