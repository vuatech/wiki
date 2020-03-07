---
title: Releases pages creation documentation
description: 
published: true
date: 2020-03-07T19:08:19.660Z
tags: documentation, wiki
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
`/releases/omlxNN/omlxNN_new`
example: /releases/omlx42/omlx42_new

#### 'Notes'
Path pattern:
`/releases/omlxNN/omlxNN_notes`
example: /releases/omlx42/omlx42_notes

#### 'Errata'
Path pattern:
`/releases/omlxNN/omlxNN_errata`
example: /releases/omlx42/omlx42_errata

## Development releases (Alpha, Beta, RC)

### subpages
Path pattern:
`/releases/omlxNN/omlxNN_alpha`
`/releases/omlxNN/omlxNN_beta`
`/releases/omlxNN/omlxNN_rc`

`/releases/omlxNN/omlxNN_alpha_notes`
`/releases/omlxNN/omlxNN_beta_notes`
`/releases/omlxNN/omlxNN_rc_notes`

`/releases/omlxNN/omlxNN_alpha_errata`
`/releases/omlxNN/omlxNN_beta_errata`
`/releases/omlxNN/omlxNN_rc_errata`

example: /releases/omlx42/omlx42_alpha
example: /releases/omlx42/omlx42_beta
example: /releases/omlx42/omlx42_rc

example: /releases/omlx42/omlx42_alpha_notes
example: /releases/omlx42/omlx42_beta_notes
example: /releases/omlx42/omlx42_rc_notes

example: /releases/omlx42/omlx42_alpha_errata
example: /releases/omlx42/omlx42_beta_errata
example: /releases/omlx42/omlx42_rc_errata

## Addendum
Paths  must be lowercase.
No punctuation allowed except dashes/hyphens and/or underscores.

Paths cannot contain the following characters:
-Space (use dashes instead)
-Period (reserved for file extensions)
-Unsafe URL characters (such as punctuation marks, quotes, math symbols, etc.)

As we often have to write release version number (4.0, 4.1, 4.2, etc.) while creating new pages just convert it into `40`, `41`, `42`, etc. by omitting the dot in the path.


