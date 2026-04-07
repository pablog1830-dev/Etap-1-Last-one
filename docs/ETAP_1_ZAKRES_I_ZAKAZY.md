# ETAP 1 — zakres i zakazy

## Źródło prawdy
Jedynym źródłem prawdy dla kodu jest plik **`Ostatnia wersja.txt`**.
Historia starego repo, stare PR-y i stare eksporty nie są źródłem prawdy o kodzie.

## Zasada nadrzędna
ETAP-1 oznacza wyłącznie:
- **refactor-only**,
- **cleanup redukcyjny**,
- **separation-only**,
- przygotowanie czystych punktów wejścia pod kolejne etapy,
- brak zmiany semantyki rdzenia.

## W ETAP-1 wolno
1. usuwać realny dead code,
2. czyścić legacy tekstowe i nazewnicze,
3. rozdzielać warstwy odpowiedzialności,
4. helperyzować techniczne duplikaty,
5. odchudzać `state / reason / blocker / dashboard / observability`,
6. porządkować granice `Decision / Quality / Scenario`,
7. porządkować granice `Execution / State / Reason / Blocker`,
8. czytelniej wydzielać `Failure / Confirm`,
9. audytować resztkową binarność,
10. zaznaczać miejsca pod kolejne etapy bez ich wdrażania.

## W ETAP-1 nie wolno
- wdrażać docelowej logiki kolejnych etapów,
- robić pełnego `liquidity event -> post-liquidity response -> survival`,
- wdrażać execution mode switching,
- wdrażać warstwy probabilistycznej,
- wdrażać ML / forecast / prediction engine,
- zmieniać **VSA core**,
- zmieniać **FVG / iteracji 1–4** biznesowo,
- zmieniać logiki `entry / exit / management` biznesowo,
- stroić progów pod wynik,
- dodawać nowych dużych warstw logicznych.

## Reguła interpretacyjna
Jeżeli nie jest oczywiste, czy zmiana jest tylko refaktoryzacją, należy przyjąć, że **nie wolno** jej wykonać w ETAP-1.
