---
title: OpenMandriva Lx 4.2 Novità
description: 
published: true
date: 2021-09-26T20:58:54.287Z
tags: 4.2
editor: markdown
dateCreated: 2020-07-17T20:23:43.002Z
---

# OpenMandriva Lx 4.2 Novità

Si raccomanda di leggere le ultime [Note di rilascio ](/en/releases/current) sul nostro wiki.

## Che cosa c'è di nuovo in OpenMandriva Lx 4.2?
OpenMandriva Lx 4.2 è una nuova release da parte della Associatione OpenMandriva. [Nome in codice](/releases/codename) Argon.

## Caratteristiche Principali

### KDE

- Frameworks 5.78.0 [*(più informazioni)*](https://www.kde.org/announcements/kde-frameworks-5.78.0.php)
- Plasma 5.20.5 [*(più informazioni)*](https://www.kde.org/announcements/plasma-5.20.5.php)
- Applications 20.12.2 [*(più informazioni)*](https://www.kde.org/announcements/announce-applications-20.12.2.php)
- Qt 5.15.2 [*(più informazioni)*](https://www.qt.io)

### Display subsystem

- Xorg 1.20.10
- Wayland 1.20.10 [*(più informazioni)*](https://wayland.freedesktop.org/releases.html)
- Mesa 20.3 [*(più informazioni)*](http://www.mesa3d.org/)

### Core

- Kernel 5.7.14 [*(più informazioni)*](https://www.kernel.org/)
- systemd 247 [*(più informazioni)*](https://www.freedesktop.org/wiki/Software/systemd/)
- LLVM/clang 11.0.1 [*(più informazioni)*](http://llvm.org/)
- gcc 10.1 [*(più informazioni)*](https://gcc.gnu.org/)
- binutils 2.36.1
- glibc 2.33 [*(più informazioni)*](http://www.gnu.org/software/libc/)
- Java 15
- Zstandard - nuovo algoritmo di compresssione in tempo reale, che fornisce alti ratei di compressione implementati nel nostro kernel, fornisce un boot più veloce.

OpenMandriva fornisce un kernel compilato con clang. L'utente può installare la stessa versione  `kernel-release-desktop` e `kernel-release-desktop-clang` per confronto.

### Installer

- Calamares 3.2.35 [*(più informazioni)*](https://calamares.io)

### Applicazioni

- LibreOffice 7.1.0
- Falkon 3.1
- Chromium browser stable 88 (e beta 89, dev 90)
- Krita 4.4.2
- Gimp 2.10.22
- Calligra Suite 3.2.1
- Digikam 7.2
- SMPlayer 21.1.0
- VLC 3.0.12
- Virtualbox 6.1.16
- OBS Studio 26.1.2
  
The port to aarch64 (64-bit ARM processors) is completed, making it possible to build [energy efficient PC replacements for less than $150](https://videos.openmandriva.org/videos/watch/4e135a39-4232-4d85-999c-e349ba8a7bd9).
Installable images are available for the PinebookPro, Raspberry Pi 4B and 3B+, Rock Pi 4A, 4B and 4C, Synquacer, Cubox Pulse and generic UEFI compatible devices, such as most aarch64 server boards. More aarch64 hardware support will follow shortly. This port also enables us to target a smartphone for the first time - an image running on the PinePhone is available (but should not yet be considered final quality).

\- 