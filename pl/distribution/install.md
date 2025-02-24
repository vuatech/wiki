---
title: Instalacja OpenMandriva Lx
description: 
published: true
date: 2024-08-20T10:30:18.197Z
tags: 
editor: markdown
dateCreated: 2021-10-02T20:03:48.871Z
---

***Jeśli masz jakiekolwiek pytania przed instalacją OpenMandriva Lx, prosimy o kontakt przez [Czat OpenMandriva](https://wiki.openmandriva.org/en/team/chat) lub na [Forum wsparcia OpenMandriva](https://forum.openmandriva.org/c/support/17).*** Ludzie mogą znajdować się w różnych strefach czasowych, więc prosimy o czas na odpowiedź.

# 1\. Przenieś pobrany obraz instalacyjny na pamięć flash USB

Do przeniesienia obrazu live/instalacyjnego na urządzenie pamięci masowej USB można użyć:
ROSA-imagewriter, KDE isoimagewriter, SUSE Studio ImageWriter, narzędzia dd w wierszu poleceń.
Nie używaj innych narzędzi do zapisu na USB, ponieważ niektóre narzędzia Windows (np. Rufus) skracają nazwę woluminu i przerywają proces rozruchu.

# 2\. Uruchamianie z pamięci flash USB

Większość komputerów automatycznie uruchamia się z pamięci USB. Wystarczy ją włożyć i włączyć komputer lub uruchomić go ponownie. Powinno pojawić się menu z prośbą o wybranie różnych pozycji.

Jeśli komputer nie uruchamia się automatycznie z USB, spróbuj przytrzymać klawisz F12 przy pierwszym uruchomieniu lub ESC. W przypadku większości komputerów pozwoli to wybrać urządzenie USB z menu rozruchowego specyficznego dla systemu.

F12 i ESC są najczęściej używanymi klawiszami do wywoływania menu startowego systemu, ale F2 i F10 są powszechnymi alternatywami. Jeśli nie masz pewności, poszukaj krótkiego komunikatu podczas uruchamiania systemu - często powie ci, który klawisz nacisnąć, aby wyświetlić menu rozruchowe.

W przeciwnym razie spróbuj znaleźć rozwiązanie w Internecie lub nie wahaj się poprosić o pomoc na naszym forum lub czacie.

## Uruchamianie z płyty DVD
Uruchamianie z płyty DVD jest przestarzałe.

# 3\. Uruchomienie OpenMandriva Lx w trybie "na żywo"

Najpierw zostaniesz poproszony o uruchomienie trybu na żywo. Uruchomi się on automatycznie po 30 sekundach. Tryb na żywo może być używany do testowania dystrybucji bez zmian na dysku komputera lub do instalowania dystrybucji.

![1](https://forum.openmandriva.org/uploads/default/optimized/2X/8/8c9727b79d2d14b3bbd0855fd324602ed1b3ff8f_2_690x283.jpeg)

Z tego menu można wybrać język i układ klawiatury. Nie ma to wpływu na układ klawiatury i język rzeczywistej instalacji, o które zostaniesz zapytany później.
 

![2](https://forum.openmandriva.org/uploads/default/optimized/2X/5/542eb029a442b16f20ddabc2b689789badd39332_2_690x322.jpeg)

Pamiętaj, że domyślnym układem klawiatury w trybie na żywo jest US QWERTY, więc może to być trudne, jeśli chcesz ustawić hasło użytkownika do instalacji bez faktycznego sprawdzania znaków. Liczba języków i układów dla trybu na żywo jest bardzo ograniczona w trybie na żywo, ale istnieje znacznie większy wybór podczas późniejszej instalacji.

![3](https://forum.openmandriva.org/uploads/default/optimized/2X/d/dc104372eed37891b803654bbe9af53fcc7dc844_2_690x322.png)

# 4\. Witamy w OpenMandriva Lx w trybie "na żywo"

![image](https://forum.openmandriva.org/uploads/default/optimized/2X/f/f834e3ba9e2380e64bdfdaa6cdb2a0f85a22905e_2_667x500.jpeg)

Możesz bezpiecznie zamknąć lub zmniejszyć okno powitalne, aby wyświetlić ikony pulpitu.

Gdy uznasz, że czas na instalację, kliknij ikonę „Zainstaluj OpenMandriva Lx”.

![image](https://forum.openmandriva.org/uploads/default/original/2X/1/152f47602da6aaec3baade2c95341ae57837247d.png)

# 5\. Przygotowanie instalacji

Najpierw wybierz język i kliknij przycisk Dalej.

![6](https://forum.openmandriva.org/uploads/default/optimized/2X/3/3ec3e0ddc0ad5c6b95d95814d54f7bd6268555ce_2_690x369.png)

Następnie wybierz strefę czasową zgodnie z [tą listą](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones#List) klikając miejsce na mapie lub korzystając z menu. Następnie sprawdź, czy język, liczby i daty są prawidłowo ustawione i kliknij przycisk Dalej.

![7](https://forum.openmandriva.org/uploads/default/optimized/2X/b/b012db7a20f89cf37474ab6b36e4476b50e1aa01_2_690x369.jpeg)

Następnie musisz wybrać układ klawiatury. Jeśli instalator nie odgadnie poprawnie domyślnego układu dla twojego języka, możesz go zmodyfikować i sprawdzić w polu „Testuj układ klawiatury”.

![8](https://forum.openmandriva.org/uploads/default/optimized/2X/6/6ffe4b3c63507fb964e06fb3679893997180bf63_2_690x369.png)

Teraz następuje najważniejszy moment instalacji, ponieważ chodzi o to, w jaki sposób system zostanie zainstalowany na dysku twardym. W zależności od tego, czy na dysku zainstalowany jest już jeden lub więcej systemów operacyjnych, instalator Calamares może zaoferować:

Kilka opcji automatycznych:

-   Zmniejsz istniejącą partycję i zainstaluj OpenMandriva Lx wraz z dowolnym innym systemem operacyjnym, już dostępnym w systemie. Jeśli masz partycję Windows, jest to opcja, którą możesz wybrać, aby zachować ten system operacyjny (zalecane dla początkujących).
-   Użycie istniejącej partycji - spowoduje zastąpienie wszystkich plików i/lub systemu operacyjnego na tej partycji nową instalacją OpenMandriva Lx (użytkownicy zaawansowani).
-   Użyj całego dysku i utwórz jedną partycję, na której wszystko zostanie zainstalowane pod rootem (administratorem, inaczej superużytkownikiem), wszystkie inne istniejące partycje zostaną usunięte (dla użytkowników początkujących).

Opcja ręcznego partycjonowania dysku:

-   Ta metoda daje ci swobodę ustawienia dowolnej opcji, dowolnego systemu plików i tablicy partycji, ale istnieje możliwość całkowitego zepsucia instalacji. Upewnij się, że wiesz, co robisz. Zostanie utworzona kolejna strona dla zaawansowanego partycjonowania. (użytkownicy-eksperci)

Wraz z wybraną opcją dostępna jest opcja "swap to file" (przestrzeń wymiany jako plik; będzie dedykowany wątek dla swap). O ile nie wiesz co robisz, "Swap to file" jest dobrą opcją.
 

![image](https://forum.openmandriva.org/uploads/default/optimized/2X/4/438b7613cbcc876b9baa212e0300071490d70ce7_2_690x143.png)

Zaznacz opcję „szyfruj system”, jeśli chcesz dodać warstwę zabezpieczeń do swoich danych. System będzie pytał o wprowadzenie ustalonego hasła przy każdym jego uruchomieniu.

![image](https://forum.openmandriva.org/uploads/default/optimized/2X/d/d0cf1db41fef4319988fa69e1e11154479761477_2_690x163.png)

Utwórz konto użytkownika, nadaj nazwę swojemu komputerowi i utwórz hasło administratora (zwane również hasłem roota) lub zaznacz opcję „użyj tego samego hasła dla konta administratora”.

![image](https://forum.openmandriva.org/uploads/default/optimized/2X/e/e46e539f893a10323d4c7bef786ac4d49807fd9f_2_690x349.png)

Po sprawdzeniu podsumowania instalacji kliknij przycisk Instaluj.

![image](https://forum.openmandriva.org/uploads/default/optimized/2X/9/92932b3faacc4819d5120defad361a7722d3be59_2_690x455.png)

Poczekaj na zakończenie procesu instalacji.

![image](https://forum.openmandriva.org/uploads/default/optimized/2X/d/dd3cb650845245a372d776b1eade5b8763fc7158_2_690x455.jpeg)

Po zakończeniu instalacji kliknij Gotowe i uruchom ponownie komputer (możesz również zaznaczyć opcję „Uruchom ponownie teraz”).

![image](https://forum.openmandriva.org/uploads/default/optimized/2X/8/8d89ea930a3998a90533d7cedb6b354d8840725d_2_690x455.png)

Po ponownym uruchomieniu komputera możesz cieszyć się korzystaniem z OpenMandriva Lx.

# Uwagi

[Źródło (forum)](https://forum.openmandriva.org/t/h/4223)

Przeczytaj także:
* [Jak utworzyć partycję root, home i swap podczas instalacji](/en/distribution/guides/how-tos/howto-root-home-swap)
* [Jak uzyskać listę wszystkich pakietów zawartych w obrazach .iso](/en/distribution/guides/how-tos/list-packages-iso)
