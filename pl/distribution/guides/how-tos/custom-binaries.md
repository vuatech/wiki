---
title: Jak skompilować własne oprogramowanie
description: 
published: false
date: 2024-01-24T01:07:05.893Z
tags: clang
editor: markdown
dateCreated: 2024-01-24T00:23:36.493Z
---

# Clang
Unikalną cechą OpenMandriva jest wykorzystanie *clang* jako głównego kompilatora. 

> GCC jest nadal dostępne, ale zostało całkowicie porzucony na rzecz CLANG od wersji 5.0 OpenMandriva.
> Nie ma możliwości używanie gcc do kompilacji modułów jądra! {.is-warning}

## Start

1. Przed skompilowaniem własnego oprogramowania należy upewnić się, że nie istnieje ono już w jednym z naszych repozytoriów.
2. Możesz również poprosić nasz zespół o dodanie pakietu na forum lub bezpośrednio na githubie

## Quick Start

Podstawowe narzędzia programistyczne można zainstalować z poziomu aplikacji OM Welcome:
![om5-welcome-devtools.png](/images/om5-welcome-devtools.png)

Z wiersza poleceń można wpisać:

```bash
sudo dnf install task-devel task-c-devel task-c++-devel
```

Przykład polecenia make służącego do skompilowania oprogramowania lokalnie na komputerze:

## Kompilator

Domyślnie oprogramowanie może używać gcc jako bazy. Musisz spróbować z clang.
Poniżej znajduje się przykład niestandardowego polecenia make

```bash
make CC=clang CXX=clang++ LD=ld.lld AR=llvm-ar NM=llvm-nm OBJCOPY=llvm-objcopy OBJSIZE=llvm-size STRIP=llvm-strip -C ...
```

## Tworzenie paczek

Jeśli chcesz pójść dalej, zapraszamy do dołączenia do naszej grupy zadaniowej zajmującej się pakietowaniem oprogramowania. 