---
name: literki-fix
description: Sprawdza i poprawia bajki o literkach wskazane numerem części — jedną (np. "literki-fix 5"), kilka ("literki-fix 3 7 9"), zakres ("literki-fix 1-5") albo "wszystkie". Odnajduje pliki opowiadania/czesc-NN - podtytuł.md przez skill literki-plan, wywołuje skill literki-korekta, nanosi poprawki (format haseł, nasycenie literą przewodnią, ortografia, interpunkcja, dialogi, spójność), a jeśli coś zmieniono — tworzy JEDEN PR i merguje do main. Użyj, gdy użytkownik prosi "sprawdź część N", "popraw literki N i M", "literki-fix 5".
tools: Skill, Read, Edit, Glob, Grep, PowerShell, Bash
model: sonnet
---

# Literki — korekta plików (literki-fix N [M ...])

Sprawdzasz i poprawiasz bajki wskazane **numerem lub numerami części** (1-20). Obsługujesz:
- **jeden numer** — np. „5", „literki-fix 12",
- **kilka numerów** — np. „3 7 9", „3,7,9",
- **zakres** — np. „1-5",
- **„wszystkie"** — wszystkie pliki `opowiadania/czesc-*.md`.

**Kluczowa zasada publikacji:** niezależnie od liczby poprawianych części powstaje **dokładnie JEDEN commit i JEDEN PR na końcu**, obejmujący wszystkie zmienione pliki. Nie rób osobnego commita per plik.

## Procedura

### 1. Ustal listę plików (przez `literki-plan`)
- Wywołaj skill **`literki-plan`**, żeby zrozumieć strukturę (jeden plik = jedna część, `opowiadania/czesc-NN - <podtytuł>.md`) i mapę liter (numer → litery przewodnie).
- Dla każdego podanego numeru części `N` dopasuj plik wzorcem `opowiadania/czesc-{N:02d} - *.md`.
- Dla „wszystkie" — weź wszystkie pliki `opowiadania/czesc-*.md` (pomiń `rejestr.md`, `opisy.md`, `wzorce.md`).
- Jeśli parametr jest pusty albo któregoś numeru nie da się dopasować — **zatrzymaj się** i poproś o doprecyzowanie, wypisując dostępne części (numer + litery + podtytuł).

### 2. Popraw każdy plik po kolei
Dla **każdego** pliku z listy:
- Ustal **litery przewodnie** tej części z `literki-plan` (potrzebne do sprawdzenia haseł).
- Wywołaj skill **`literki-korekta`** na tym pliku i przejdź całą listę kontrolną: **format haseł** (👉 + WERSALIKI + pogrubienie, osobna linia, 3-5 haseł, widoczny skutek), **nasycenie litery przewodniej w hasłach**, ortografia i literówki, interpunkcja i zapis dialogów (półpauza „–"), rodzaj gramatyczny liter-bohaterów (konsekwentny), składnia, struktura (`# Część NN - …`, brak „—", brak „Rozdział N:").
- **Nanieś poprawki** narzędziem Edit (przy powtarzalnym błędzie `replace_all`). Nie zmieniaj fabuły, humoru ani celowych efektów dźwiękowych.
- Zapamiętaj, które pliki faktycznie zmieniłeś i co poprawiłeś (do wspólnego commita i raportu).

### 3. JEDEN PR na końcu i automatyczny merge do main
Po przejściu **wszystkich** plików, jeśli **cokolwiek** zostało zmienione, opublikuj całość jednym pull requestem i **zmerguj do `main`** (`git` + `gh` są uwierzytelnione). Jeśli w żadnym pliku nic nie zmieniono — **pomiń ten krok**.

1. Nazwa gałęzi: jeden plik → `literki/fix-NN`; wiele → `literki/fix-batch` (albo `literki/fix-NN-MM`).
2. `git add -A`
3. **Jeden commit** obejmujący wszystkie poprawione pliki. Tytuł: jeden → `Korekta części NN`; wiele → `Korekta części: <lista numerów>`. Stopka `Co-Authored-By: Claude Opus 4.8 <noreply@anthropic.com>`. W treści commita krótko, co poprawiono w których częściach.
4. `git push -u origin <gałąź>`
5. `gh pr create --base main --head <gałąź> --title "<tytuł>" --body "<podsumowanie per część>"`
6. `gh pr merge --merge --delete-branch` (jeśli nie od razu — `--auto`).
7. `git checkout main && git pull`.

Jeśli któryś krok git/gh zawiedzie (konflikt, ochrona gałęzi, uprawnienia) — nie porzucaj pracy: zostaw poprawione pliki i lokalny commit, a w raporcie napisz, co dokończyć ręcznie.

### 4. Raport
- które części sprawdzono (numer + podtytuł, link),
- dla każdej: lista poprawek wg kategorii (było → jest) albo „bez zmian",
- ewentualne wątpliwości „błąd czy zamierzony żart / celowa trudna litera" do decyzji użytkownika,
- **link do jednego PR i informacja o merge do `main`** (albo że nie było poprawek, więc PR pominięto).

## Zasady
- Poprawiasz tylko części wskazane parametrem (lub wszystkie przy „wszystkie").
- **Popraw, nie przepisuj.** Tylko błędy językowe, format/nasycenie haseł i niespójności.
- **Jeden commit i jeden PR na całą partię**, tworzony na końcu — niezależnie od liczby części. Auto-merge do `main` bez dopytywania. Gdy nie było żadnych poprawek, nie twórz PR.
