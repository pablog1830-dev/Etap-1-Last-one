# Repo operating model

## Cel
To repo ma pozwalać na pracę z tego okna przez branch, PR, diff i pełny plik kanoniczny.

## Zasady pliku kanonicznego
- istnieje **jeden** główny pełny plik `.pine`
- każda iteracja modyfikuje właśnie ten plik
- nie utrzymujemy wielu równoległych wersji roboczych jako alternatywnych źródeł prawdy

## Ścieżki docelowe
- `src/ITER_04A_SCALP_4A_MANIPULATION_PHASE_CORRECTION_FULL.pine` — plik kanoniczny
- `audit/FULL_COPY__ITER_04A_SCALP_4A_MANIPULATION_PHASE_CORRECTION_FULL.pine` — kopia 1:1 do audytu
- `docs/*` — zasady, zakres, checklisty, audyty

## Reguła FULL COPY
Po każdej iteracji:
1. główny plik `.pine` jest aktualizowany
2. `FULL_COPY` jest synchronizowany 1:1
3. PR raportuje `COPY_OK` albo rozjazd

## Reguła iteracji
Każda iteracja musi kończyć się:
1. opisem dokładnie co zmieniono
2. opisem czego celowo nie ruszono
3. bilansem netto
4. kontrolą zakresu ETAP-1
5. audytem lokalnym iteracji
6. próbą potwierdzenia poprawności
7. werdyktem `PASS / PARTIAL / FAIL`

## Reguła audytu końcowego
Na końcu iteracji ma powstać wszechstronny audyt obejmujący:
- zgodność iteracji z zakresem
- zgodność z wcześniejszymi iteracjami
- poprawność logiczną
- miejsca ryzyka
- wpływ na pełny plik
- wynik prób i kontroli

## Reguła branchy
- `e1-a1-*` dla baseline i synchronizacji
- `e1-b1-*` dla dead-code cleanup
- `e1-b2-*` dla semantic cleanup
- `e1-c1-*` dla separation Decision/Quality/Scenario
- `e1-c2-*` dla separation Execution/State/Reason/Blocker
- `e1-c3-*` dla separation Failure/Confirm
- `e1-d1-*` dla audytu binarności
- `e1-e1-*` dla extension points
- `e1-f1-*` dla final full audit
