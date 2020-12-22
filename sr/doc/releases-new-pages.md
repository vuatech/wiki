---
title: Објављује документацију за креирање страница
description: 
published: true
date: 2020-04-10T19:38:31.399Z
tags: 
---

# Објављује документацију за креирање страница

За свако ново издање, треба креирати:

## Финално издање (GA)

### главна страница 'Преглед'

Шема путање:
`/releases/omlxNN`
пример: /releases/omlx42

### подстранице
#### 'Шта је ново?'
Шема путање:
`/releases/omlxNN/new`
пример: /releases/omlx42/new

#### 'Напомене'
Шема путање:
`/releases/omlxNN/notes`
пример: /releases/omlx42/notes

#### 'Уочени проблеми'
Шема путање:
`/releases/omlxNN/errata`
пример: /releases/omlx42/errata

## Развојна изадања (Алфа, Бета, RC)

### подстранице
Шема путање:
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

пример: /releases/omlx42/alpha/notes
пример: /releases/omlx42/beta/notes
пример: /releases/omlx42/rc/notes

пример: /releases/omlx42/alpha/errata
пример: /releases/omlx42/beta/errata
пример: /releases/omlx42/rc/errata

## Додатак - Путање
Путања мора бити са малим словима. Користи средњу црту за раздвајање речи.
Тачке нису дозвољене осим средње/доње црте и/или подвлачења.

Путање не могу садржати следеће симболе:
- Празан простор (уместо тога користи средњу црту)
- Тачку (резервисана за екстензије фајлова)
- Небезбедне URL карактере (попут двотачке, наводника, математичких симбола, итд.)

Како обично морамо да напишемо број за верзију издања (4.0, 4.1, 4.2, итд), када креирамо нове странице ово обично конвертујемо у `40`, `41`,`42`, итд. избацујући тачку у путањи.

