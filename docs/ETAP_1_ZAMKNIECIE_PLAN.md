# ETAP 1 — plan zamknięcia

## Źródło prawdy
Za obowiązujący baseline kodu uznaje się wyłącznie plik **`Ostatnia wersja.txt`**.
Docelowo jego treść ma zostać utrzymywana jako pełny plik kanoniczny `.pine` w repo.

## Lista działań potrzebnych do zamknięcia ETAP-1
1. finalny **dead-code cleanup**
2. **semantic cleanup**
3. separation-only: **Decision / Quality / Scenario**
4. separation-only: **Execution / State / Reason / Blocker**
5. separation-only: **Failure / Confirm**
6. audyt resztkowej **binarności**
7. oznaczenie punktów wejścia pod kolejne etapy
8. finalny **full audit** całego pliku

## Zasada końcowa
Niezależnie od tego, jaki punkt jest wykonywany lokalnie, na końcu trzeba sprawdzić cały plik względem pełnej listy 1–8.

## Model pracy na GitHub
- **1 punkt = 1 branch = 1 PR**
- żadnych szerokich PR-ów wielotematycznych
- żadnych zmian „przy okazji”
- każdy PR ma dotyczyć wyłącznie jednego punktu

## Zasada pełnego pliku w diff
Repo ma być prowadzone tak, aby:
- diff pokazywał **patch iteracji**,
- ale jednocześnie w repo był zawsze dostępny **pełny aktualny plik**,
- po każdej iteracji istniała też **pełna kopia audytowa 1:1**.

## Warunek zamknięcia ETAP-1
ETAP-1 można uznać za zamknięty dopiero wtedy, gdy:
- baseline jest zsynchronizowany jako pełny plik kanoniczny,
- wykonano punkty 1–8,
- przeprowadzono końcowy audyt całej iteracji i całego pliku,
- końcowy werdykt brzmi: `ETAP 1 READY FOR NEXT-STAGE SYNTHESIS`.
