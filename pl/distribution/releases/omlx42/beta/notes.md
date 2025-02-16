---
title: OpenMandriva Lx 4.2 Beta Uwagi do wydania
description: 
published: true
date: 2021-09-26T20:57:22.085Z
tags: 4.2
editor: markdown
dateCreated: 2020-03-07T17:10:54.689Z
---

# OpenMandriva Lx 4.2 Beta Uwagi do wydania

> Ostrzeżenie: Wydanie [beta](/releases/software-release-life-cycle#beta)  nie jest przeznaczone do użytku w środowisku produkcyjnym. Wydanie przeznaczone do testów i wyszukiwania błędów. Z pewnością zawiera błędy  i będzie powodować problemy. Jeśli pobierzesz i przetestujesz ten produkt, zgłoś swoje odkrycia i problemy na naszej stronie [Forum](http://forum.openmandriva.org/) or at [Github Issues](https://github.com/OpenMandrivaAssociation/OpenMandrivaAssociation.github.io/issues).
{.is-warning}


## Dostępne nośniki
To wydanie jest dostępne jako płyta DVD live media lub pamięć flash USB (pendrive), do pobrania w formacie ISO. Pliki są dostępne na naszej stronie [pobierz](https://www.openmandriva.org/download). Instalacja z pamięci USB jest zwykle zauważalnie szybsza. Jak zawsze szybkość zależy od wielu czynników.
*Live media* oznacza możliwość uruchomienia OpenMandriva Lx bezpośrednio z DVD lub pendrive'a (patrz poniżej) i wypróbowania go przed instalacją. Można również zainstalować system na dysku twardym z uruchomionego obrazu na żywo lub z menedżera rozruchu.

Dostępne pliki ISO 
- x86_64 [KDE Plasma](https://www.kde.org/plasma-desktop) w pełni funkcjonalny pulpit (zawiera najczęściej używane funkcje, multimedia i oprogramowanie biurowe).
- znver1 Plasma: stworzyliśmy również wersję specjalnie dla obecnych procesorów AMD (Ryzen, ThreadRipper, EPYC), która przewyższa wydajnościowo wersję ogólną (x86_64), na tych procesorach  wykorzystując ich nowe funkcje.
znver1 jest przeznaczony wyłącznie dla wymienionych procesorów (Ryzen, ThreadRipper, EPYC), nie należy go instalować na żadnym innym sprzęcie.

## Wymagania systemowe

OpenMandriva Lx 4.2 wymaga co najmniej 2048 MB pamięci i co najmniej 10 GB miejsca na dysku twardym (poniżej znane problemy z partycjonowaniem).

> Ważna uwaga: Sprzęt graficzny: 
> KDE Plasma Desktop wymaga karty graficznej 3D obsługującej OpenGL 2.0 lub wyższy.
> Zalecamy używanie układów graficznych AMD, Intel, Adreno lub VC4s.
{.is-warning}

## Połączenie z internetem

Instalator Calamares sprawdza, czy dostępne jest połączenie z Internetem, ale system OpenMandriva Lx 4 zainstaluje się bez problemów nawet bez niego.  System będzie funkcjonować normalnie
Aktualizacja takiego systemu wymagać będzie tymczasowego połączenia z Internetem lub pobrania pakietów w innym miejscu i przeniesienia ich do zainstalowanego systemu oraz, instalacji zaktualizowanych pakietów. Nawet bez podłączenia do Internetu, możesz po prostu korzystać z systemu i nie aktualizować go przez dowolny czas.

## Maszyny wirtualne
Obecnie jedynym oprogramowaniem do wirtualizacji, na którym testowane są ISO OMLx, jest VirtualBox. Te same wymagania sprzętowe dotyczą uruchamiania na maszynach wirtualnych.
Jednak w przypadku VirtualBox musisz **zawsze** mieć co najmniej 2048 MB pamięci, w przeciwnym razie OpenMandriva Lx nie uruchomi się.
Również w przypadku VirtualBox zaleca się instalację na świeżej maszynie wirtualnej, ponieważ próba instalacji na istniejącej może zakończyć się niepowodzeniem.

## Instalator Calamares

Calamares to framework instalatora.
Z założenia jest elastyczny, konfigurowalny, co pozwala dostosować go do różnych potrzeb i przypadków użycia. Z założenia ma być: łatwy, użyteczny, ładny, pragmatyczny, spójny i niezależny od dystrybucji.
Calamares zawiera zaawansowaną funkcję partycjonowania, z obsługą zarówno ręcznych, jak i automatycznych operacji partycjonowania. 
Jest to pierwszy instalator z automatyczną opcją „Zastąp partycję”, która ułatwia wielokrotne używanie partycji przy testowaniu dystrybucji.
Wiele dystrybucji Linuksa korzysta z instalatora Calamares, a każda z nich posiada własną implementację i standardy. Fakt, że coś w instalatorze OpenMandriva nie jest zgodne z doświadczeniami użytkownika z inną dystrybucją Linuksa nie oznacza, że jest to błąd.

## Partycjonowanie

W tej chwili partycjonowanie LVM i konfiguracje Raid za pomocą instalatora Calamares nie są obsługiwane.
**Dotyczy to wszystkich partycjonowań**, wszystkich instalacji na sprzęcie: Jeśli masz komputer UEFI/EFI, a BIOS oferuje wybór podczas uruchamiania nośnika instalacyjnego między np:

niektóre `USB Flash Drive`
niektóre `UEFI USB Flash Drive`
oraz
`niektóre  DVD optical_device`
niektóre `UEFI DVD optical_device`

Musisz wybrać opcję UEFI i ją uruchomić. Należy jednak pamiętać, że nie wszystkie komputery będą to robić. Niektóre z bardziej spartańskim BIOS-em będą oferować tylko jedną opcję i prawie zawsze będzie to ta właściwa. Na przykład, jeśli na notebooku nie widzisz powyższego wyboru, nie martw się.
Jeśli masz włączonych wiele dysków, wszystkie muszą mieć ten sam typ tablicy partycji. Wszystkie muszą być gpt lub mbr, aby wszystko działało poprawnie. 
Na komputerach UEFI w sytuacji multi-boot z wieloma dyskami, jeśli masz już istniejącą partycję `/boot/efi`, musisz jej użyć. Partycjoner nie utworzy kolejnej partycji `/boot/efi` z odpowiednimi flagami i instalacja zakończy się błędem z braku zainstalowanego bootloadera. Nie formatuj partycji ustaw punkt jedynie punkt montowania na `/boot/efi`. Można mieć wiele różnych bootloaderów dla różnych systemów operacyjnych na tej samej partycji `/boot/efi`. Jeśli istnieje potrzeba przełączenia bootloadera, można to zrobić w ustawieniach BIOS-u.

## NVME SSD

Niektóre dyski SSD NVME mogą nie być rozpoznawane przez OMLx 4.2 *Live* ISO.
ISO *Live* ma 2 różne obejścia tego problemu w sekcji „Rozwiązywanie problemów” w menu Grub2. Są to `(PCIE ASPM=OFF)` i `(NVME APST=OFF)`. Mamy nadzieję, że zadziała to na większości sprzętów. Problem jest znany i pracują nad nim deweloperzy OpenMandriva i deweloperzy upstream. Zobacz więcej w [4.2/Errata#NVME SSDs](/releases/omlx42/beta/errata#nvme-ssds).
Rozpoznawanie sprzętu dla dysków SSD nvme powinno zostać znacznie ulepszone. Wiadomo, że niektóre dyski Samsung nvme SSD, które wcześniej nie były rozpoznawane, są teraz rozpoznawane w tej wersji jądra. Problem ten jest bardzo specyficzny dla sprzętu.

## Instalator i wsparcie EFI 

To wydanie OpenMandriva Lx  uruchamia się i instaluje z oraz bez [UEFI](https://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface).
SECURE BOOT NIE jest obsługiwany.
Jeśli chcesz przeprowadzić instalację EFI na istniejącym dysku MBR, konieczne będzie przekonwertowanie tablicy partycji dysku na nowszy schemat partycjonowania GPT. Aby to zrobić, należy użyć narzędzia gdisk. Typowe wywołanie to `gdisk /dev/sda`: istniejąca tablica partycji zostanie przekonwertowana do schematu GPT. Zostaną wyświetlone ostrzeżenia o potencjalnej utracie danych, dysk nie zostanie nadpisany do czasu zapisania tablicy partycji przez naciśnięcie przycisku <kbd>w</kbd>. Zaleca się wykonanie kopii zapasowej ważnych danych.
Może się zdarzyć, że konwersja nie będzie mogła zostać przeprowadzona, zwykle będzie to spowodowane niewystarczającą ilością miejsca na początku lub na końcu dysku, aby zapisać tablicę partycji. Może być konieczne usunięcie lub zmiana rozmiaru partycji, aby utworzyć potrzebne miejsce, gparted jest przydatnym narzędziem w takiej sytuacji . 
Podczas uruchamiania instalatora Calamares, należy utworzyć partycję rozruchową uefi. Gdy instalator dojdzie do etapu partycjonowania, partycja `/` (root) powinna zostać usunięta, a na początku dysku powinna zostać utworzona mała (330 MB) partycja FAT16 lub FAT32. Jeśli przestrzeń dyskowa jest krytyczna, można użyć mniejszej partycji, ale należy pamiętać, aby ustawić ją jako FAT16 lub FAT32 w Calamares, w przeciwnym razie instalacja zakończy się niepowodzeniem.
W przypadku nieprzestrzegania tych kroków instalacja programu rozruchowego nie powiedzie się. Następnie należy podzielić dysk na partycje w normalny sposób.
Prosimy o podzielenie się swoimi doświadczeniami na forum, abyśmy mogli poprawić ten aspekt instalacji.
Jeśli instalujesz obok Windows 8, 8.1, 10 lub podobnego systemu operacyjnego uruchamianego przez EFI, jako środek ostrożności upewnij się, że masz dysk odzyskiwania i wykonałeś kopię zapasową wszystkich ważnych danych. 
Przeprowadzane przez nas testy były ograniczone do tej konfiguracji, ale udało się przeprowadzić udane instalacje bez żadnych problemów. Będziemy wdzięczni za wszelkie opinie w tym zakresie.

## Zmiana typu partycji

Należy pamiętać, że Calamares nie może przekonwertować jednego typu partycji na inny przy jednoczesnym zachowaniu danych partycji.
W przypadku uruchomienia programu Calamares z obrazu live nie jest możliwa zmiana istniejącego typu partycji. Próba wykonania tej czynności spowoduje wygenerowanie komunikatu o błędzie. 
Aby to zrobić, należy najpierw usunąć istniejącą partycję i utworzyć ją ponownie jako żądany typ.

## Bootowanie - rozruch z USB

Możliwe jest również uruchomienie instalacji z urządzenia pamięci masowej USB.  Można:

### - Użyć ROSA Image Writer dostępnego z repozytorium

`sudo dnf --refresh install rosa-imagewriter`

Jeśli nie masz jeszcze OpenMandriva Lx, możesz pobrać ROSA Image Writer na [tej stronie](http://wiki.rosalab.ru/en/index.php/ROSA_ImageWriter).
Zalecane jest użycie pamięći flash o pojemności co najmniej 4 GB. Pamięć trwała nie jest konieczna. Należy pamiętać, że wszystkie istniejące dane zostaną **usunięte** z pamięci  USB i zastąpione obrazem  OpenMandriva Lx

> Nie używaj innych narzędzi do zapisu na USB, ponieważ niektóre narzędzia Windows (np. Rufus) obcinają nazwę woluminu. Powoduje to przerwanie procesu rozruchu.
{.is-danger}

### - Via dd

Można użyć dd do utworzenia obrazu na USB:
`$ sudo dd if=<iso_name> of=<usb_drive> bs=4M status=progress conf=fsync`

Zastąp `<iso_name>` ścieżką do ISO i `<usb_drive>` nazwą urządzenia blokowego pamięci USB  np:. `/dev/sdb`.

SUSE Studio ImageWriter  również został przetestowany,  można nim nagrywać ISO na USB. 
Działa z obrazami ISO Open Mandriva Lx

## Bootowanie / uruchamianie z pliku ISO

Wpis Grub2, do dodania w `/boot/grub2/grub.cfg`
```
submenu "OpenMandriva (64 bit)" {
        set isofile=/home/user/OpenMandrivaLx.4.2-plasma.x86_64.iso
        set isoname=OpenMandrivaLx_4.2
        loopback loop $isofile

        menuentry "OpenMandriva" {
                linux (loop)/boot/vmlinuz0 root=live:LABEL=${isoname} iso-scan/filename=${isofile} rd.live.image toram --
                initrd (loop)/boot/liveinitrd.img
        }
}
```

## O repozytoriach

Mamy teraz [om-repo-picker](/images/omlx4.1-repo-picker.jpg) aka Software Repository Selector, aby wybrać dodatkowe repozytoria dla większej dostępności pakietów.
Nie należy mieszać repozytoriów z różnych wersji/kanałów aktualizacji. Oznacza to, na przykład, **nie używanie repozytoriów Cooker w systemie Rock**. Jeśli używasz Rock, używaj tylko repozytoriów Rock.
Jest to wyjaśnione bardziej szczegółowo w [OpenMandriva harmonogram wydań i repozytoriów](/doc/release-plan-and-repositories). 
**Jeśli mieszasz różne repozytoria kanału wydań/aktualizacji i zepsujesz komputer, rozwiązaniem jest wykonanie nowej instalacji**. Po tej świeżej instalacji nie rób tego ponownie.

## Jak instalować nowe pakiety
Podczas gdy narzędzia graficzne (Discover, dnfdragora itp.) są przydatne do wyszukiwania dostępnego dodatkowego oprogramowania, zdecydowanie zalecamy instalowanie pakietów z wiersza poleceń:
`$ sudo dnf --refresh install <package_name>`

## Jak aktualizować system
Należy pamiętać, że w wersjach rozwojowych „Kanał aktualizacji” jest domyślnie ustawiony na Rolling.
Zalecanym poleceniem do aktualizacji systemu Rolling jest:
`$ sudo dnf clean all ; sudo dnf --allowerasing distro-sync`.

## Najważniejsze / główne zmiany i nowe funkcje

Aby być na bieżąco z najnowszymi zmianami w systemie Linux, kwestiami bezpieczeństwa komputerowego i pisaniem kodu komputerowego, w OMLx 4.2 wprowadzono poważne zmiany.

Najważniejsze zmiany
- Kernel linux zaktualizowano do 5.10.2
- Bibliotekę Qt zaktualizowano do 5.15.2
- Zaktualizowano Plasma: Frameworks 5.77.0, Plasma Desktop 5.20.4, Aplikacje 20.12.0
- *Więcej informacji w* [co nowego](/en/releases/omlx42/new)


# Errata
See [4.2/Alpha/Errata](/en/releases/omlx42/beta/errata).

