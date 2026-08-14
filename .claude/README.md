# Generatory bajek o literkach (Claude Code)

Ten katalog zawiera skille i agentów [Claude Code](https://claude.com/claude-code) do pisania interaktywnego cyklu **„Bajki o literkach"** w spójnym stylu. Ładują się automatycznie, gdy Claude Code działa w tym repo.

Cykl ma **stały plan 20 części** (opisany w [`info/idea.md`](../info/idea.md)) — **każda część to jedna bajka** ucząca innej litery lub grupy liter. To bajki **do czytania naprzemiennego**: rodzic czyta płynnie fabułę, a dziecko czyta **magiczne hasła** (👉 WERSALIKAMI, pogrubione), bez których akcja nie ruszy dalej. Hasła są nasycone literą przewodnią danej części — to ćwiczenie czytania w przebraniu zabawy.

Opowiadania leżą w `opowiadania/` jako pojedyncze pliki `czesc-NN - <podtytuł>.md`. Mapą liter i umiejscowieniem zarządza skill **`literki-plan`**.

## Skille — [`skills/`](skills)

- [**literki-generuj**](skills/literki-generuj/SKILL.md) — pełna, interaktywna bajka: świat literek → problem → 3-5 haseł-bramek dla dziecka (nasyconych literą przewodnią) → kulminacja → ciepły morał. Tekst rodzica ~200-300 słów prozą; hasła w formacie 👉 + WERSALIKI + pogrubienie.
- [**literki-pomysly**](skills/literki-pomysly/SKILL.md) — szkielet twórczy jednej części: motyw/kraina, litery-bohaterowie, propozycje haseł, morał (bez pisania całości).
- [**literki-korekta**](skills/literki-korekta/SKILL.md) — sprawdza i poprawia gotowy tekst: **format i nasycenie haseł**, ortografia, interpunkcja, zapis dialogów, spójność rodzaju liter-bohaterów. Poprawia, nie przepisuje.
- [**literki-plan**](skills/literki-plan/SKILL.md) — źródło prawdy o strukturze: stały plan 20 części, mapa numer → litery przewodnie, ścieżka pliku. Używany przez agentów.
- [**literki-druk**](skills/literki-druk/SKILL.md) — wersja do druku **PDF/DOCX**. PDF czysto w Pythonie (reportlab) — **bez Worda i bez drukarki**; klikalny spis treści, zakładki (część→scenka) i **wyróżnione ramki z hasłami**. Parametry: `--typ pdf|docx|oba`, `--czesc N|calosc|wszystko` (domyślnie PDF najnowszej części).

Wywołanie w Claude Code: `/literki-generuj`, `/literki-pomysly`, `/literki-korekta` — opcjonalnie z numerem części.

## Agenci — [`agents/`](agents)

- [**literki-fabryka**](agents/literki-fabryka.md) — pisze części; tryb zależy od parametru:
  - **bez parametru** → następna niezrobiona część **z review** (pokazuje motyw, litery-bohaterów i propozycje haseł; „Akceptuj wszystko" albo dopytywanie po kolei),
  - **numer części N (1-20)** → ta konkretna część, z review,
  - **kilka numerów / zakres / `wszystko`** → partia **z automatu, bez review** (jeden zbiorczy PR).

  Umiejscowienie i litery przez `literki-plan`. Przed commitem robi **korektę** (`literki-korekta`), aktualizuje `README.md`, `rejestr.md`, `opisy.md` i **automatycznie tworzy PR + merge do `main`**.

- [**literki-fix**](agents/literki-fix.md) — sprawdza i poprawia części wskazane numerem: jedną (`literki-fix 5`), kilka (`literki-fix 3 7 9`), zakres (`literki-fix 1-5`) lub `wszystkie`. Odnajduje pliki przez `literki-plan`, woła `literki-korekta`, a na końcu **tworzy PR i merguje do `main`** — przy wielu częściach **jeden wspólny commit/PR**. Gdy nic nie wymaga poprawy, PR pomija.

- [**literki-druk**](agents/literki-druk.md) — buduje plik do druku (PDF/DOCX). Domyślnie PDF najnowszej części; parametry `typ` i `czesc`. **Bez Worda/drukarki** (reportlab). Zapisuje do `druk/` (nieśledzone), wysyła pliki.

- [**literki-do-druku**](agents/literki-do-druku.md) — finalizacja całości **jednym przebiegiem**: korekta wszystkich części (`literki-korekta`, ewentualny PR) → generacja PDF do `druk/` → **kontrola jakości druku** (każdy rozdział > 1,5 strony; w całym PDF tylko jeden krój, Arial, zero Helvetiki). Użyj przed oddaniem do druku.

Wywołanie: poproś Claude Code o użycie agenta `literki-fabryka` (opcjonalnie z numerem/`wszystko`), `literki-fix N` / `literki-fix N M …`, albo `literki-druk N`.

## Modele
- **Domyślnie Sonnet** (ustawiony we frontmatterze agentów) — wystarcza do części łatwych/średnich (1-14).
- **Trudne części (15-20**, festiwale liter 18-19 i **Wielki Finał 20**) — uruchamiaj `literki-fabryka` na **Opusie** (override modelu przy wywołaniu) albo Sonnecie ze wzmocnioną korektą haseł. Powód: trzeba upchać dużo liter przewodnich w hasła, zachować sens i humor, nie męcząc 6-latka.

## Wspólne zasady stylu
- Język polski, proste słowa; **absurdalny humor** dla 6-latka + drobne mrugnięcie do dorosłego.
- **Czytanie naprzemienne:** rodzic — fabuła; dziecko — 3-5 haseł (👉 WERSALIKAMI, pogrubione) nasyconych literą przewodnią.
- Litery są **bohaterami** z charakterem z kształtu i dźwięku (A śpiewa, S syczy, Ł w kapeluszu z daszkiem…).
- Narracja/tytuły — łącznik „-" (nigdy „—"); dialogi od półpauzy „–".
- Zawsze bezpiecznie i ciepło; morał prosty i pozytywny.

## Struktura

```
.claude/
├─ README.md
├─ skills/
│  ├─ literki-generuj/SKILL.md
│  ├─ literki-pomysly/SKILL.md
│  ├─ literki-korekta/SKILL.md
│  ├─ literki-plan/SKILL.md
│  └─ literki-druk/ (SKILL.md + build_pdf.py)
└─ agents/
   ├─ literki-fabryka.md
   ├─ literki-fix.md
   ├─ literki-druk.md
   └─ literki-do-druku.md
```

> Uwaga: w odróżnieniu od serii „po 10 opowiadań na zbiór", tu **jeden plik = jedna część** i plan jest **stały (20 pozycji)**. Dlatego nie ma skilla `split` (zastępuje go `literki-plan`) ani krótkiej formy — każda część musi mieć pełną strukturę z hasłami.
