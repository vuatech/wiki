---
title: OpenMandriva Lx 4.2 Alpha Errata
description: 
published: true
date: 2021-09-26T20:55:57.359Z
tags: 4.2
editor: markdown
dateCreated: 2020-02-27T16:13:04.324Z
---

# OpenMandriva Lx 4.2 Alpha Errata - Znane problemy
> Podobnie jak w przypadku każdej wersji, nadal istnieją błędy i usterki, które mogły nie zostać rozwiązane. Ta strona dokumentuje te, które mogą powodować niedogodności, a tam, gdzie to możliwe, szczegółowo opisuje, jak można je obejść.
{.is-info}


**Zaleca się przeczytanie najnowszych** [informacji o wydaniu](https://wiki.openmandriva.org/en/releases/omlx42/alpha/notes) **na naszej wiki**.

## Karty graficzne NVIDIA
To wydanie zawiera sterownik nouveau, który zapewnia umiarkowanie dobre wsparcie dla większości kart NVIDIA. W przypadku pracy na dwóch ekranach jest on lepszy niż binarny sterownik NVIDIA, ponieważ obsługuje obracanie ekranu na drugim monitorze, co jest przydatne w przypadku monitorów z obracanymi ekranami.
Użytkownicy mogą korzystać ze sterowników ze strony nvidia, ale nie są one obsługiwane przez OpenMandriva. Nie mogą one być obsługiwane przez OpenMandriva z wielu powodów.
Instalowanie i utrzymywanie jakichkolwiek sterowników nVidia pozostaje w wyłącznej gestii  i odpowiedzialności użytkownika.

## NVME SSDs
Istnieje dobrze znany problem z niektórymi (zwłaszcza nowszymi) dyskami NVME SSD i urządzeniami PCIE, w których dysk SSD może nie zostać rozpoznany. Dla naszego *Live* ISO istnieje obejście opisane w [Uwagach do wydania](/releases/omlx41/notes).
Problem jest znany i pracują nad nim deweloperzy OpenMandriva jak i deweloperzy upstream.
Rozpoznawanie sprzętu dla dysków SSD nvme powinno zostać znacznie poprawione. 
Wiadomo, że niektóre dyski Samsung nvme SSD, które wcześniej nie były rozpoznawane, są teraz rozpoznawane w tej wersji jądra. Problem ten jest oczywiście bardzo specyficzny dla sprzętu.

W przypadku zainstalowanego systemu można zastosować obejście w `/etc/default/grub`, następnie zastosować`update-grub2` by uczynić zmianę globalną. Obejście znalezione na, dotyczy *Live* ISO.

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
Włącz drukarkę i sprawdź, czy została automatycznie skonfigurowana. Zwróć uwagę, czy został zainstalowany odpowiedni sterownik. Jeśli drukarka została skonfigurowana automatycznie i masz prawidłowy sterownik, świetnie! Wszystko gotowe.
Jeśli drukarka nie została wykryta. 
1.Wyłącz drukarkę. 
2.Otwórz *Ustawienia drukarki*, czyli `system-config-printer` i usuń drukarkę.
Jeśli domyślnie nie został zainstalowany właściwy sterownik,zainstalujemy go "ręcznie".

Następnym krokiem jest określenie, jakie oprogramowanie dodać dla twojej drukarki.

W OpenMandriva Lx będzie to najprawdopodobniej  pakiet 'task-printing' zależny od producenta twojej drukarki. Dostępne są następujące pakiety:
- task-printing-canon
- task-printing-epson
- task-printing-hp
- task-printing-lexmark
- task-printing-okidata
- task-printing-misc

Zainstaluj pakiet odpowiedni dla twojego producenta drukarki lub pakiet misc jeżeli żaden inny nie pasuje. W przykładzie użyto okidata:
```
$ sudo dnf install task-printing-okidata
```
Włącz drukarkę ponownie, powinna automatycznie się skonfigurować. Czasami może być konieczne ponowne uruchomienie, aby automatyczna konfiguracja działała.

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

## Znane problemy nad którymi obecnie pracujemy

Nasz system śledzenia błędów ma pewne problemy, dlatego prosimy o zgłaszanie nowych błędów na naszym [Forum](https://forum.openmandriva.org/) lub
w [Github Issues](https://github.com/OpenMandrivaAssociation/OpenMandrivaAssociation.github.io/issues)

Raportuj błąd przez system śledzenia błędów OpenMandriva :

- [Cooker Host: VirtualBox 6.1.12 VM's nie startuje](https://issues.openmandriva.org/show_bug.cgi?id=2634)

- [VBox plasma desktop crash (virtualbox-guest-additions)](https://issues.openmandriva.org/show_bug.cgi?id=2633)

- [Brak dzwięku przy logowaniu (lub dźwięk nieprawidłowy) Plasma 5.19.3, KF 5.72.0](https://issues.openmandriva.org/show_bug.cgi?id=2629)

- [Zmiany punktu montowania w KDE Partition Manager nie są zapisywane w /etc/fstab (DOTYCZY WSZYSTKICH WERSJI OM Lx)](https://issues.openmandriva.org/show_bug.cgi?id=2628)

- [OM-Control-Center nie działa z Wayland (Cooker)](https://issues.openmandriva.org/show_bug.cgi?id=2625)

- [Aktualizacja jednej gałęzi jądra do innej gałęzi jądra o tym samym numerze wersji nie powiodła się](https://issues.openmandriva.org/show_bug.cgi?id=2619)

- [grub2-editor (kcm_grub2) „Nie udało się zapisać ustawień GRUB.” Błąd backendu DBus. (WSZYSTKIE wersje OM Lx)](https://issues.openmandriva.org/show_bug.cgi?id=2618)

- [Samba nie działa](https://issues.openmandriva.org/show_bug.cgi?id=2609)

Błędy zgłoszone w Github Issues:  (Problemy Github)

- [Użytkownik musi dwukrotnie wprowadzić hasło do wifi (uszkodzony NM aplet) #53].(https://github.com/OpenMandrivaAssociation/OpenMandrivaAssociation.github.io/issues/53)


