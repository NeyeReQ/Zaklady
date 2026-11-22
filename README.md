# Arena Desk — panel zakładów PvP

Ciemny panel operatora w stylistyce Launchera Kwadratowy Chaos. Służy do ręcznego zapisywania zakładów na pojedynki Team 1 vs Team 2. Nie wymaga Minecrafta, pluginów, API ani serwera backendowego.

## Uruchomienie

- Otwórz `index.html` w przeglądarce albo opublikuj repozytorium przez GitHub Pages.
- Aby włączyć GitHub Pages: **Settings → Pages → Deploy from a branch → main → /(root)**.
- Dane zapisują się w `localStorage` przeglądarki, z której korzystasz.

## Funkcje

- Ręczne dodawanie nicku gracza, stawki i wybranej drużyny.
- Lista wszystkich wpisanych kuponów z wyszukiwarką graczy.
- Dynamiczne kursy puli, aktualizowane po każdej zmianie stawek.
- Konfigurowalna prowizja operatora (domyślnie 10%).
- Zamknięcie przyjmowania zakładów i zablokowanie zmian w kuponach.
- Wskazanie zwycięskiej drużyny i automatyczne wyliczenie wypłat.
- Łączenie kuponów tego samego nicku w jedną końcową wypłatę.
- Zaokrąglanie do pełnych monet metodą największych reszt — suma wypłat zgadza się dokładnie z pulą.
- Anulowanie pojedynku z przygotowaniem zwrotu stawek bez pobierania prowizji.
- Historia rund, eksport CSV rozliczenia oraz import/eksport kopii JSON.

## Zasady obliczeń

Dla całej puli (P), prowizji (c) i sumy stawek na zwycięską drużynę (S):

- Pula wypłat: `floor(P × (1 − c/100))`
- Kurs dziesiętny: `pula wypłat / S`
- Wypłata: `stawka gracza na zwycięską drużynę × kurs`

Wypłata zawiera zwrot stawki. Jeśli zwycięska drużyna nie ma żadnych zakładów, nie można wyliczyć wypłat — można anulować pojedynek i przygotować zwrot wszystkich stawek.

## Ważne ograniczenia

To statyczna wersja dla jednego operatora i jednej przeglądarki. Dane **nie synchronizują się** między komputerami i nie są przechowywane na serwerze. Przed zmianą urządzenia lub czyszczeniem danych przeglądarki pobierz kopię JSON.

Panel jest wyłącznie kalkulatorem i rejestrem. Nie łączy się z Minecraftem, nie wymaga żadnej wtyczki i nie wysyła monet automatycznie — samodzielnie wpisujesz graczy, stawki i realizujesz wypłaty.
