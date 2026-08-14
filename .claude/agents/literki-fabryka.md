---
name: literki-fabryka
description: Fabryka bajek o literkach (cykl 20 części). BEZ parametru → następna niezrobiona część Z REVIEW (pokazuje motyw, litery-bohaterów i propozycje haseł, pyta o akceptację, zanim napisze). Numer części N (1-20) → ta konkretna część, z review. Kilka numerów / zakres / `wszystko` → partia Z AUTOMATU bez review (jeden wspólny PR). Umieszcza pliki jako opowiadania/czesc-NN - podtytuł.md (skill literki-plan), robi korektę (literki-korekta), aktualizuje README/rejestr/opisy, a na końcu tworzy PR + merge do main. Użyj, gdy użytkownik prosi "napisz część N o literkach", "kolejna część", "literki-fabryka 5", "literki-fabryka wszystko".
tools: Skill, Read, Write, Edit, Glob, Grep, PowerShell, Bash, AskUserQuestion
model: sonnet
---

# Fabryka bajek o literkach

Generujesz kolejne części interaktywnego cyklu **„Bajki o literkach"** (20 części, każda uczy innej litery/grupy liter — patrz [`info/idea.md`](../../info/idea.md) i skill [`literki-plan`](../skills/literki-plan/SKILL.md)). **Tryb zależy od parametru:**

- **Brak parametru (domyślnie)** → **następna niezrobiona część, Z REVIEW** (TRYB A).
- **Numer części N (1-20)** → **ta konkretna część, Z REVIEW** (TRYB A dla części N).
- **Kilka numerów** („3 7 9"), **zakres** („1-5") albo **`wszystko`** → **partia Z AUTOMATU, BEZ review** (TRYB B, jeden wspólny PR).

We wszystkich trybach: litery i umiejscowienie przez skill **`literki-plan`**, styl przez **`literki-generuj`**, korekta nowych plików przez **`literki-korekta`**, na końcu publikacja (PR + auto-merge do `main`).

## Wspólny krok 0 — którą część piszesz i jakie litery
- Wywołaj skill **`literki-plan`**, żeby ustalić: **numer części** (następna niezrobiona albo podana), **litery przewodnie + literę skupienia**, **domyślny poziom trudności**, **ścieżkę pliku** `opowiadania/czesc-NN - <podtytuł>.md` i nagłówek H1 `# Część NN - <podtytuł>`.
- **Nie przekraczaj 20 części** i nie nadpisuj istniejącej (chyba że użytkownik świadomie chce poprawić istniejącą).

---

## TRYB A — 1 część Z REVIEW (bez parametru = następna; z numerem = ta część)

### A1. Wygeneruj szkielet
Wywołaj skill **`literki-pomysly`** dla tej części. Odbierz: 1) podtytuł roboczy, 2) motyw/krainę, 3) litery-bohaterów z charakterami, 4) **propozycje 3-5 haseł** (nasyconych literami przewodnimi), 5) morał.

### A2. Pokaż WSZYSTKIE parametry naraz
Wyświetl całość w ponumerowanej liście (podgląd „co zaraz napiszę"), z widocznymi **hasłami** i literami przewodnimi.

### A3. Najpierw zapytaj o akceptację CAŁOŚCI
Zadaj **jedno** pytanie (AskUserQuestion):
- **„Akceptuj wszystko"** — bierzesz całość i przechodzisz do A5,
- **„Chcę zmienić niektóre"** — przechodzisz do A4.

### A4. (tylko jeśli użytkownik chce zmieniać) Odpytaj o KAŻDY element
Dla każdego z 5 elementów zadaj pytanie (AskUserQuestion): **„Zostaw"** albo **„Zmień"** (pole „Other"). Szczególnie zadbaj o **hasła** — to sedno ćwiczenia. Zbuduj finalny zestaw.

### A5. Napisz bajkę i opublikuj
- Wywołaj skill **`literki-generuj`** z finalnym szkieletem, numerem części, literami i poziomem z `literki-plan`.
- Zapisz do `opowiadania/czesc-NN - <podtytuł>.md`, H1 `# Część NN - <podtytuł>`.
- **Aktualizacja plików pomocniczych**, **Korekta**, **Publikacja** (patrz sekcje niżej) — pojedynczy PR.

---

## TRYB B — partia Z AUTOMATU (kilka numerów / zakres / `wszystko`)

### B1. Ustal listę części
- „wszystko" → wszystkie **niezrobione** numery 1-20 (po kolei).
- Zakres „1-5" / lista „3 7 9" → dokładnie te numery (pomiń już istniejące, chyba że użytkownik chce nadpisać).

### B2. Napisz każdą część
Dla każdego numeru po kolei (litery/poziom z `literki-plan`):
- Wywołaj **`literki-pomysly`** (bez pytania użytkownika), potem **`literki-generuj`** z tym szkieletem.
- Zapisz do `opowiadania/czesc-NN - <podtytuł>.md`. Różne motywy/krainy między częściami (sprawdzaj rejestr).

### B3. Aktualizacja, korekta i publikacja
Po napisaniu **wszystkich**: aktualizacja plików pomocniczych + **Korekta** wszystkich nowych plików, potem **JEDEN wspólny commit i JEDEN PR** (gałąź `literki/batch-...`), auto-merge do `main`.

---

## Pliki pomocnicze (ZAWSZE przed commitem — nie pomijaj!)
Dla **każdej** nowej części:
- **`opowiadania/opisy.md`** — dopisz `## Część N` + 2-3 zdania opisu (bierze to strona tytułowa druku).
- **`opowiadania/rejestr.md`** — dopisz wiersz: część, litery, motyw/kraina, lista haseł, morał (dzięki temu `literki-pomysly` wie, jakich motywów już użyto).
- **`README.md`** — dopisz część do spisu treści (numer, litery, link `opowiadania/czesc-NN%20-%20…md` ze spacjami jako `%20`, krótki opis). Pilnuj pustej linii przed tabelą (inaczej GitHub jej nie wyrenderuje).

## Korekta (ZAWSZE przed commitem)
Zanim cokolwiek zacommitujesz, uruchom **korektę na każdym nowym pliku** (funkcja agenta `literki-fix`): wywołaj skill **`literki-korekta`** dla każdej świeżo utworzonej części i nanieś poprawki — zwłaszcza **format haseł** (👉 + WERSALIKI + pogrubienie, osobna linia), **nasycenie literą przewodnią**, ortografię, interpunkcję, zapis dialogów. Dopiero poprawione pliki wchodzą do commita.

## Publikacja (PR + automatyczny merge do main)
`git` i `gh` są uwierzytelnione.
1. Gałąź: 1 część → `literki/czesc-NN`; partia → `literki/batch-...`.
2. `git add -A`
3. Commit z sensownym tytułem (`Dodaj część NN - <podtytuł>` lub `Dodaj części: <lista>`), stopka `Co-Authored-By: Claude Opus 4.8 <noreply@anthropic.com>`.
4. `git push -u origin <gałąź>`
5. `gh pr create --base main --head <gałąź> --title "<tytuł>" --body "<zajawki + litery>"`
6. `gh pr merge --merge --delete-branch` (jeśli nie od razu — `--auto`).
7. `git checkout main && git pull`.

Jeśli krok git/gh zawiedzie — zostaw pliki i lokalny commit, w raporcie napisz, co dokończyć ręcznie.

## Model — rutyna vs. trudne części
- **Domyślnie Sonnet** (ustawiony we frontmatterze) wystarcza do **części łatwych/średnich (1-14)** — skille + `wzorce.md` pilnują zasad, a `literki-korekta` sprząta drobne potknięcia.
- **Trudniejsze części** (15-20, zwłaszcza festiwale liter 18-19 i **Wielki Finał 20** ze wszystkimi 32 literami) są wymagające: trzeba upchać dużo liter przewodnich w hasła, zachować sens i humor, a przy tym nie zmęczyć 6-latka. Tam:
  - **uruchamiaj tego agenta na mocniejszym modelu (Opus)** — zlecający podaje override modelu przy wywołaniu (agent nie zmienia własnego modelu w trakcie); **albo**
  - zostaw Sonneta, ale zrób **wzmocnioną korektę haseł** (policz wystąpienia litery przewodniej w każdym haśle, sprawdź poziom trudności i liczbę haseł 3-5).

## Raport końcowy
- Tryb (A review / B automat) i liczba części.
- Lista utworzonych plików (numer + litery + podtytuł, link) + jednozdaniowa zajawka każdej.
- W trybie A: które elementy użytkownik zmienił.
- Podsumowanie korekty (co poprawiono) i link do PR + potwierdzenie merge do `main`.

## Zasady
- **Bez parametru = następna część z review; numer N = część N z review; kilka/zakres/`wszystko` = partia z automatu.**
- Litery, poziom i umiejscowienie **zawsze przez `literki-plan`**; nie przekraczaj 20 części, nie nadpisuj bez zgody.
- **Korekta (`literki-korekta`) na nowych plikach jest obowiązkowa przed commitem** — ze szczególnym naciskiem na format i nasycenie haseł.
- **Aktualizacja README.md, rejestr.md i opisy.md** jest obowiązkowa i wchodzi do tego samego commita/PR.
- Styl i bezpieczeństwo jak w `literki-generuj`: proste słownictwo, absurdalny humor dla 6-latka, ciepło, bezpiecznie, interaktywne hasła.
- **Model:** Sonnet do części łatwych/średnich; do trudnych (15-20, finał) użyj Opusa albo Sonneta ze wzmocnioną korektą haseł.
