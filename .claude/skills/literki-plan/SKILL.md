---
name: literki-plan
description: Źródło prawdy o strukturze cyklu "Bajki o literkach" — stały plan 20 części, mapowanie numer części → litery przewodnie oraz umiejscowienie/ścieżka pliku opowiadania (opowiadania/czesc-NN - podtytuł.md). Używany przez agentów literki-fabryka (gdzie zapisać nową część, jakie litery) i literki-fix (odnalezienie pliku części po numerze). Wywołaj, gdy trzeba ustalić litery danej części albo ścieżkę pliku.
---

# literki-plan — struktura cyklu i mapa liter

Jedyne źródło prawdy o tym, **jak zbudowany jest cykl „Bajki o literkach"** i **gdzie leży (lub trafia) opowiadanie danej części**. W odróżnieniu od zwykłej serii, tu **plan jest STAŁY: dokładnie 20 części**, a **każda część to JEDNA bajka** ucząca konkretnej litery lub grupy liter (patrz [`info/idea.md`](../../../info/idea.md)). Agenci wołają ten skill, żeby ustalić litery przewodnie i ścieżkę pliku.

## Struktura katalogów

```
opowiadania/
├─ czesc-01 - <podtytuł>.md   # Część 1 — jedna bajka (litery A, O)
├─ czesc-02 - <podtytuł>.md   # Część 2 (litery E, I)
├─ …
├─ czesc-20 - <podtytuł>.md   # Część 20 — Wielki Finał
├─ rejestr.md                 # co już napisano (część, litery, motyw, hasła, morał)
├─ opisy.md                   # 2-3 zdania opisu każdej części (strona tytułowa druku)
└─ wzorce.md                  # pule fraz do rotacji (dźwięki, otwarcia, skutki haseł)
```

- **Jeden plik = jedna część.** Nazwa: `czesc-NN - <podtytuł>.md`, gdzie `NN` = numer części **dwucyfrowo z zerem** (`czesc-01` … `czesc-20`).
- Nagłówek H1 w pliku: `# Część NN - <podtytuł>` (numer części + zabawny podtytuł, separator to łącznik `-`, nigdy „—").
- `rejestr.md`, `opisy.md`, `wzorce.md` to **nie** są opowiadania — pomijaj je przy liczeniu i przy druku.

## Mapa liter (STAŁA — z `info/idea.md`, nie zmieniaj)

| Część | Litery | Skupienie | Motyw z planu |
|------:|--------|-----------|----------------|
| 1  | A, O | A | Śpiewające siostry i aparatowe awarie |
| 2  | E, I | E | Sprytna E i smukła I |
| 3  | U, Y | U | Wielkie zamieszanie na końcu alfabetu |
| 4  | Ą, Ę | — | Dwie litery z ogonkami jak pędzelki |
| 5  | L, Ł | Ł | Prosta L i Ł w kapeluszu z daszkiem |
| 6  | C, Ć | Ć | Cichy C i Ć z piórkiem na głowie |
| 7  | S, Ś | Ś | Sycząca S i Ś szepcząca jak wiatr |
| 8  | Z, Ż, Ź | Ż, Ź | Trzej bracia Z (zwykły, z kropką, z kreską) |
| 9  | O, Ó | Ó | Zwykłe O i Ó z kreską |
| 10 | B, P | B | Dwaj brzuchaci budowniczowie |
| 11 | D, T | D | Stukający i pukający bliźniacy |
| 12 | G, K | K | Gotowanie i kląskanie |
| 13 | M, N | M | Dwa wzgórza M i jedno wzgórze N |
| 14 | R, W | R | Warczące R i szybka W |
| 15 | F, H | F | Fukające F i zasapane H |
| 16 | J | J | Samotne J skaczące jak haczyk na ryby |
| 17 | Ń (i N) | Ń | Cichutkie Ń chowające się za innymi |
| 18 | Ź, Ć, Ś, Ń | — | Wielki Festiwal Miękkich Liter z Kreskami |
| 19 | Ą, Ę, Ń | — | Grupa „Trudne Początki" (litery, od których nie zaczynają się słowa) |
| 20 | wszystkie 32 | — | Wielki Finał — Budowa Słownikowego Królestwa |

**Litery przewodnie** danej części = kolumna „Litery"; **litera do szczególnego ćwiczenia** = kolumna „Skupienie" (jeśli podana). Hasła dla dziecka mają być nasycone przede wszystkim literą ze „Skupienia", a poza tym pozostałymi literami przewodnimi.

## Poziom trudności wg numeru (domyślny)

- **Części 1-5 → ŁATWY** (hasła 2-3 krótkie słowa, proste sylaby otwarte).
- **Części 6-14 → TRUDNIEJSZY** (3-4 słowa, dwuznaki/miękkości, dłuższe wyrazy).
- **Części 15-20 → NAJTRUDNIEJSZY** (dłuższe hasła, więcej słów, celowe zbitki liter przewodnich).

Użytkownik może nadpisać poziom niezależnie od numeru.

## Gdzie trafia KOLEJNA część (placement)

1. Wylistuj pliki `opowiadania/czesc-*.md` (pomiń `rejestr.md`, `opisy.md`, `wzorce.md`) i odczytaj z nazw, które numery części `NN` już istnieją.
2. **Następna do napisania** = najniższy numer `1..20`, którego jeszcze **nie ma** (domyślnie idź po kolei 1, 2, 3…). Jeśli użytkownik podał konkretny numer części — użyj jego.
3. Zwróć: numer części `NN`, litery przewodnie i skupienie (z mapy wyżej), domyślny poziom trudności, pełną ścieżkę pliku `opowiadania/czesc-NN - <podtytuł>.md` oraz nagłówek H1 `# Część NN - <podtytuł>`.
4. **Nie przekraczaj 20** i **nie duplikuj** istniejącego numeru (chyba że użytkownik świadomie chce nadpisać/poprawić istniejącą część).

## Odnalezienie pliku po numerze (dla korekty/druku)

Numer części `N` (1-20) → wzorzec `opowiadania/czesc-{N:02d} - *.md`, dopasuj istniejący plik. „wszystkie" → wszystkie pliki `opowiadania/czesc-*.md`.

## Nowy plik — pamiętaj (obowiązki wokół zapisu)
Gdy powstaje nowa część:
- dopisz jej **opis** (2-3 zdania) do `opowiadania/opisy.md` (`## Część N`) — bierze go strona tytułowa druku,
- dopisz **wiersz do rejestru** `opowiadania/rejestr.md` (część, litery, motyw, hasła, morał),
- zaktualizuj `README.md` (spis części) i sekcję w `.claude/README.md`, jeśli trzeba.

## Zasady
- Numery części **zawsze dwucyfrowo z zerem** (`01`…`20`).
- **Plan jest stały: 20 części, litery wg mapy** — nie zmieniaj przypisania liter do numeru.
- Jeden plik = jedna część; nie twórz folderów-zbiorów (to nie ten typ serii co „po 10 na zbiór").
- Nie zostawiaj luk w numeracji, chyba że użytkownik świadomie pisze części nie po kolei.
