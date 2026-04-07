# ETAP 1 — standard audytu końcowego iteracji

## Każda iteracja obowiązkowo kończy się audytem
Audyt ma potwierdzić nie tylko sam patch, ale też poprawność pełnego pliku po patchu.

## Audyt iteracji musi objąć
1. **zakres** — czy iteracja nie wyszła poza wskazany punkt
2. **semantykę** — czy nie zmieniono logiki biznesowej poza zakresem
3. **spójność** — czy teksty, reason, blocker, state odpowiadają realnej logice
4. **regresję lokalną** — czy nie cofnięto wcześniejszych ustaleń
5. **pełny plik** — czy aktualny pełny `.pine` nadal jest wewnętrznie spójny
6. **FULL_COPY** — czy kopia 1:1 zgadza się z plikiem kanonicznym
7. **próby / kontrole** — jakie wykonano sprawdzenia i jaki dały wynik

## Minimalna struktura raportu po iteracji
- branch
- zakres punktu
- HEAD before
- HEAD after
- lista zmian
- czego nie ruszono
- bilans netto
- wynik prób i kontroli
- COPY_OK / rozjazd
- werdykt `PASS / PARTIAL / FAIL`

## Audyt finalny całego ETAP-1
Na końcu ETAP-1 trzeba dodatkowo wykonać audyt całego pliku obejmujący:
- Inputs / helpers
- feature layer
- VSA core
- HTF/LTF
- liquidity / zones
- background
- decision core
- setup / entry
- position management
- dashboard / UI / alerts
- scenario / modifier / reason
- helpery techniczne

## Zasada rygoru
Nie wolno uznać iteracji za poprawną tylko dlatego, że patch wygląda sensownie. Ocena ma dotyczyć także pełnej wersji pliku po zmianie.
