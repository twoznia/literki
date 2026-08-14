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

*(jeszcze pusty — pierwsza część zostanie dopisana przez `literki-fabryka`)*

| Część | Litery | Podtytuł |
|------:|--------|----------|
| — | — | *(brak)* |
