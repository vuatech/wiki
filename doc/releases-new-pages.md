---
title: Releases pages creation documentation
description: 
published: true
date: 2020-12-21T23:52:20.803Z
tags: 
editor: undefined
dateCreated: 2020-03-07T18:55:42.072Z
---

# Releases pages creation documentation

For every new release, to be created:

## Final release (GA)

### main page 'Overview'

Path pattern:
`/releases/omlxNN`
example: /releases/omlx42

### subpages
#### 'What's New?'
Path pattern:
`/releases/omlxNN/new`
example: /releases/omlx42/new

#### 'Notes'
Path pattern:
`/releases/omlxNN/notes`
example: /releases/omlx42/notes

#### 'Errata'
Path pattern:
`/releases/omlxNN/errata`
example: /releases/omlx42/errata

## Development releases (Alpha, Beta, RC)

### subpages
Path pattern:
`/releases/omlxNN/alpha`
`/releases/omlxNN/beta`
`/releases/omlxNN/rc`

`/releases/omlxNN/alpha/notes`
`/releases/omlxNN/beta/notes`
`/releases/omlxNN/rc/notes`

`/releases/omlxNN/alpha/errata`
`/releases/omlxNN/beta/errata`
`/releases/omlxNN/rc/errata`

example: /releases/omlx42/alpha
example: /releases/omlx42/beta
example: /releases/omlx42/rc

example: /releases/omlx42/alpha/notes
example: /releases/omlx42/beta/notes
example: /releases/omlx42/rc/notes

example: /releases/omlx42/alpha/errata
example: /releases/omlx42/beta/errata
example: /releases/omlx42/rc/errata

## Addendum - Paths
Paths  must be lowercase. Use dashed to separate the words.
No punctuation allowed except dashes/hyphens and/or underscores.

Paths cannot contain the following characters:
-Space (use dashes instead)
-Period (reserved for file extensions)
-Unsafe URL characters (such as punctuation marks, quotes, math symbols, etc.)

As we often have to write release version number (4.0, 4.1, 4.2, etc.), while creating new pages just convert it into `40`, `41`, `42`, etc. by omitting the dot in the path.

