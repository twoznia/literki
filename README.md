# Bajki o literkach 🔤

Interaktywny cykl bajek edukacyjnych **do czytania naprzemiennego** dla 6-latka, który zna litery i dopiero uczy się czytać. **Rodzic czyta płynnie fabułę, a dziecko czyta magiczne hasła** (👉 WERSALIKAMI, pogrubione), bez których akcja nie ruszy dalej. Hasła są nasycone literą przewodnią danej części — czytanie w przebraniu zabawy.

Cykl ma **stały plan 20 części** ([`info/idea.md`](info/idea.md)) — każda część to jedna bajka ucząca innej litery lub grupy liter. Litery są bohaterami z charakterem z ich kształtu i dźwięku (A śpiewa, S syczy, Ł nosi kapelusz z daszkiem…).

## Jak to napisane

W repo działają skille i agenci [Claude Code](https://claude.com/claude-code) (patrz [`.claude/README.md`](.claude/README.md)):

- **`literki-generuj`** — styl i schemat pełnej, interaktywnej bajki.
- **`literki-pomysly`** — szkielet twórczy części (motyw, litery-bohaterowie, hasła).
- **`literki-korekta`** — korekta języka i formatu haseł.
- **`literki-plan`** — mapa numer części → litery i umiejscowienie pliku.
- **`literki-druk`** — wersja do druku PDF/DOCX (reportlab, bez Worda/drukarki).
- Agenci: **`literki-fabryka`** (pisze + korekta + PR/merge), **`literki-fix`** (korekta + PR/merge), **`literki-druk`** (plik do druku).

## Struktura

```
info/idea.md              # brief i plan 20 części (źródło prawdy o literach)
opowiadania/
├─ czesc-NN - <podtytuł>.md  # jedna część = jedna bajka
├─ rejestr.md             # co już napisano
├─ opisy.md               # opisy części (strona tytułowa druku)
└─ wzorce.md              # pule fraz do rotacji
.claude/                  # skille i agenci Claude Code
```

## Spis części

| Część | Litery | Podtytuł |
|------:|--------|----------|
| 1 | A, O | [Śpiewające siostry A i O](opowiadania/czesc-01%20-%20%C5%9Apiewaj%C4%85ce%20siostry%20A%20i%20O.md) |
| 2 | E, I | [Sprytna E i smukła I](opowiadania/czesc-02%20-%20Sprytna%20E%20i%20smuk%C5%82a%20I.md) |
| 3 | U, Y | [Wielkie zamieszanie na końcu alfabetu](opowiadania/czesc-03%20-%20Wielkie%20zamieszanie%20na%20ko%C5%84cu%20alfabetu.md) |
| 4 | Ą, Ę | [Ogonkowa pracownia Ą i Ę](opowiadania/czesc-04%20-%20Ogonkowa%20pracownia%20%C4%84%20i%20%C4%98.md) |
| 5 | L, Ł | [Prosta L i Ł w kapeluszu](opowiadania/czesc-05%20-%20Prosta%20L%20i%20%C5%81%20w%20kapeluszu.md) |
| 6 | C, Ć | [Cichy C i Ć z piórkiem](opowiadania/czesc-06%20-%20Cichy%20C%20i%20%C4%86%20z%20pi%C3%B3rkiem.md) |
| 7 | S, Ś | [Sycząca S i szepcząca Ś](opowiadania/czesc-07%20-%20Sycz%C4%85ca%20S%20i%20szepcz%C4%85ca%20%C5%9A.md) |
| 8 | Z, Ż, Ź | [Trzej bracia Z, Ż i Ź](opowiadania/czesc-08%20-%20Trzej%20bracia%20Z%2C%20%C5%BB%20i%20%C5%B9.md) |
| 9 | O, Ó | [Zwykłe O i Ó z kreską](opowiadania/czesc-09%20-%20Zwyk%C5%82e%20O%20i%20%C3%93%20z%20kresk%C4%85.md) |
| 10 | B, P | [Brzuchaci budowniczowie B i P](opowiadania/czesc-10%20-%20Brzuchaci%20budowniczowie%20B%20i%20P.md) |
