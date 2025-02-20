---
title: OpenMandriva Lx 4.2 Beta Errata
description: 
published: true
date: 2021-11-18T03:14:04.096Z
tags: 4.2
editor: markdown
dateCreated: 2020-03-07T17:15:26.926Z
---

# OpenMandriva Lx 4.2 Beta Errata - Znane problemy
> Podobnie jak w przypadku każdej wersji, nadal istnieją błędy i usterki, które mogły nie zostać rozwiązane. Ta strona dokumentuje te, które mogą powodować niedogodności, a tam, gdzie to możliwe, szczegółowo opisuje, jak można je obejść.
{.is-info}

Zaleca się przeczytanie najnowszych** [informacji o wydaniu] (/releases/omlx42/beta/notes) na naszej stronie wiki.

## Karty graficzne NVIDIA
To wydanie zawiera sterownik nouveau, który zapewnia umiarkowanie dobre wsparcie dla większości kart NVIDIA. W przypadku pracy na dwóch ekranach jest on lepszy niż binarny sterownik NVIDIA, ponieważ obsługuje obracanie ekranu na drugim monitorze, co jest przydatne w przypadku monitorów z obracanymi ekranami.
Użytkownicy mogą korzystać ze sterowników ze strony nvidia, ale nie są one obsługiwane przez OpenMandriva. Nie mogą one być obsługiwane przez OpenMandriva z wielu powodów.
Instalowanie i utrzymywanie jakichkolwiek sterowników nVidia pozostaje w wyłącznej gestii  i odpowiedzialności użytkownika.

## NVME SSD
Istnieje dobrze znany problem z niektórymi (zwłaszcza nowszymi) dyskami SSD NVME i urządzeniami PCIE, w których dysk SSD może nie zostać rozpoznany.
Problem jest znany i pracują nad nim deweloperzy OpenMandriva i deweloperzy upstream.
Rozpoznawanie sprzętu dla dysków SSD nvme zostało znacznie poprawione. 
Wiadomo, że niektóre dyski Samsung nvme SSD, które wcześniej nie były rozpoznawane, są teraz rozpoznawane w tej wersji jądra. Problem ten jest oczywiście bardzo specyficzny dla sprzętu.

W przypadku zainstalowanego systemu można  zastosować obejście w  `/etc/default/grub`, następnie zastosować`update-grub2` by uczynić zmianę globalną. Obejście znalezione na, dotyczy *Live* ISO.

Jeżli `(PCIE ASPM=OFF)` działa dodaj:
`pcie=aspm=off`
do następujących linii:
`GRUB_DECLINE_LINUX_DEFAULT`
`GRUB_DECLINE_LINUX_RECOVERY`
w 
`/etc/default/grub` 
następnie wydaj polecenie:
`$ sudo update-grub2`

Jeżeli `(NVME APST=OFF)` zamiast tego dodaj:
`nvme_core.default_ps_max_latency_us=0`

Jeżeli czegoś nie rozumiesz, zadaj pytanie na [forum](https://forum.openmandriva.org/).

## GEOIP
Automatyczne ustawienia GEOIP z instalatora mogą wykryć strefę czasową w sposób niepoprawny.

## Jak skonfigurować drukarkę
Włącz drukarkę i sprawdź, czy została automatycznie skonfigurowana. Zwróć uwagę, czy został zainstalowany właściwy sterownik. Jeśli drukarka została automatycznie skonfigurowana i masz prawidłowy sterownik, to świetnie, wszystko gotowe.
Jeśli nie, wyłącz drukarkę. Otwórz *Printer Settings* aka SystemSettings>Hardware>Printers i usuń drukarkę. Możesz również uzyskać dostęp do *Ustawień drukarki* z Konsole (terminal) za pomocą:

```
$ kcmshell5 kcm_printer_manager
```

Jeśli prawidłowy sterownik nie został zainstalowany domyślnie, będziemy musieli dodać pakiet oprogramowania.

Następnym krokiem jest określenie, jakie oprogramowanie dodać dla twojej drukarki.

W OpenMandriva Lx będzie to najprawdopodobniej  pakiet 'task-printing' zależny od producenta twojej drukarki. Dostępne są następujące pakiety:
- task-printing-canon
- task-printing-epson
- task-printing-hp
- task-printing-lexmark
- task-printing-okidata
- task-printing-misc

Install the package that matches your brand or the misc package if none do. Example using okidata:
```
$ sudo dnf install task-printing-okidata
```
Now turn printer on again and it should then automatically configure itself (sometimes you might need to reboot for auto config to work).

Jeżeli nadal nie działa zadaj pytanie, kliknij w link [tu](https://forum.openmandriva.org/c/en/support)

## Discover
W przypadku oprogramowania znajdującego się w repozytoriach Discover może nie wyświetlać wszystkich dostępnych pakietów.
Dzieje się tak z powodu niewyczyszczonej pamięci podręcznej discover oraz braku pobrania listy repozytoriów przy pierwszym uruchomieniu.
Rozwiązanie jest następujące: uruchom polecenia
```
$ sudo rm -rf /var/cache/PackageKit/* /var/cache/app-info/*
$ sudo pkcon refresh force
```
Jeśli dodać także dodatkowe repozytoria pakietów, musisz je włączyć za pomocą [Software Repository Selector](/en/doc/repositories-tldr) i  odświeżyć pamięć podręczną.

## Multiboot
W „prawdziwym świecie” multiboot zwykle dobrze działa, ale gdy pojawiają się problemy, czasami  najlepszym rozwiązaniem jest obejście obejście problemu. Tak to z multibotem bywa.

OpenMandriva QA nie ma możliwości testowania bootloadera z każdym typem systemu plików, w każdej dystrybucji Linuksa, ani nawet w „10 najpopularniejszych” dystrybucji. Niezależnie od tego, czy to multiboot Windows, czy inną dystrybucją Linuksa, polegamy wyłącznie na raportach użytkowników. Z tych właśnie raportów dowiadujemy się co działa, a co nie w przypadku osób stosujących multibooting.

Jednym ze znanych problemów napotykanych w programu ładującego OM Lx jest to, że OM Lx grub2 nie tworzy wpisów rozruchowych dla systemów openSUSE korzystających z systemu plików btrfs. OM Lx grub2 działa z systemami openSUSE korzystającymi z systemu plików ext4.
Dzieje się tak, ponieważ openSUSE używa niestandardowej składni dla swoich łatek  na btrfs dla pakietów openSUSE os-prober i grub2, które nie są kompatybilne z kodem OM Lx. Obecnie nie wiadomo, czy bootloader OM Lx działa/nie działa z openSUSE i innymi typami systemów plików, takimi jak XFS lub F2FS.

Rozwiązaniem jest przełączenie programów rozruchowych w ustawieniach oprogramowania układowego UEFI lub BIOS-ie.
Alternatywą może być użycie programu ładującego openSUSE, jeśli rozpoznaje on twóją OpenMandrive.
Gdy użytkownicy zgłaszają problemy z multibootem, naprawimy to, co jesteśmy w stanie. Problemy, których nie jesteśmy w stanie rozwiązać, ogłaszamy w Erratach do wydań OM Lx.

<br>

## Znane problemy nad którymi obecnie pracujemy

### Logowanie do Plasma desktop in VirtualBox
W VirtualBox szybkie wylogowanie i/lub zalogowanie może spowodować wyświetlenie czarnego ekranu na pulpicie Plasma.
Błąd dotyczy przede wszystkim trybu Live, ale czasami zauważano go również w przypadku zainstalowanego systemu.
Jako obejście, należy odczekać co najmniej 5 sekund na ekranie wylogowania sddm i to samo dotyczy logowania.

......





