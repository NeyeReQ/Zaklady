# Arena Desk — panel zakładów PvP

Lekki, samodzielny panel do ręcznej ewidencji zakładów na pojedynki Team 1 vs Team 2. Aplikacja nie wymaga instalowania zależności ani uruchamiania backendu.

## Uruchomienie

- Otwórz `index.html` w przeglądarce albo opublikuj repozytorium przez GitHub Pages.
- Aby włączyć GitHub Pages: **Settings → Pages → Deploy from a branch → main → /(root)**.
- Wszystkie dane są przechowywane w `localStorage` przeglądarki, w której otwarto panel.

## Funkcje

- Dodawanie zakładów przez nick, stawkę i wybór drużyny.
- Dynamiczne kursy puli aktualizowane po każdym dodaniu lub usunięciu kuponu.
- Konfigurowalna prowizja operatora (domyślnie 10%).
- Zamknięcie przyjmowania zakładów i zablokowanie zmian w kuponach.
- Wskazanie zwycięskiej drużyny i automatyczne rozliczenie graczy.
- Łączenie kilku kuponów tego samego nicku w jedną wypłatę.
- Zaokrąglanie do pełnych monet metodą największych reszt — suma wypłat zgadza się dokładnie z pulą.
- Anulowanie pojedynku z przygotowaniem zwrotu stawek bez pobierania prowizji.
- Historia zakończonych rund, eksport CSV wypłat oraz import/eksport kopii JSON.

## Zasady obliczeń

Dla sumy stawek (P), prowizji (c) i sumy stawek na daną drużynę (S):

- Pula wypłat: `floor(P × (1 − c/100))`
- Kurs dziesiętny: `pula wypłat / S`
- Szacowana lub końcowa wypłata: `stawka gracza × kurs`

Wypłata obejmuje zwrot postawionej stawki. Gdy na zwycięską drużynę nie przyjęto żadnego kuponu, rozliczenie nie jest możliwe — można anulować pojedynek i przygotować zwrot wszystkich stawek.

## Ważne ograniczenia

To wersja statyczna, przeznaczona dla jednego operatora korzystającego z jednej przeglądarki. Dane **nie synchronizują się** między komputerami ani operatorami i nie są przechowywane na serwerze. Przed zmianą urządzenia lub czyszczeniem danych przeglądarki pobierz kopię JSON. Aplikacja wylicza rozliczenia, ale nie łączy się z ekonomią Minecrafta i nie wysyła monet automatycznie — wypłaty realizuje operator na serwerze.
